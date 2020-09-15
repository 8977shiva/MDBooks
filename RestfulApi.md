routes

middleware

```javascript
const mongoose=require('mongoose');


const PostSchema=mongoose.Schema({
 username:{
     type:String,
     required:true
 },
 email:{
     type:String,
     required:true
 },
 password:String,
});

module.exports=mongoose.model('Rest', PostSchema);
```





```javascript
const router = require("express").Router(); //2
const Post = require("../models/post");

router.get("/", (req, res) => {
  res.send("homepage");
});

router.get("/get", async (req, res) => {
  try {
    const posts = await Post.find();
    res.json(posts);
  } catch (err) {
    res.json({ message: err });
  }
});
router.post("/post", async (req, res) => {
  console.log(req.body);
  const post = new Post({
    username: req.body.username,
    email: req.body.email,
    password: req.body.password,
  });
  try {
    const savedpost = await post.save();
    res.json(savedpost);
  } catch (err) {
    res.json({ message: err });
  }
});

//specific post
router.get("/get/:username", async (req, res) => {
  console.log(req.params.username)
  try {
    const post = await Post.find({ username: req.params.username });
    res.json(post);
  } catch (err) {
    res.json({ message: err });
  }
});

//Delete post
router.delete("/:username", async (req, res) => {
  try {
    const removedPost = await Post.remove({ username: req.params.username });
    res.json(removedPost);
  } catch (err) {
    res.json({ message: err });
  }
});

// Upadte
router.patch("/patch/:username", async (req, res) => {
  try {
    const updatePost = await Post.updateOne(
      { username: req.params.username },
      {
        $set: { password: req.body.password },
      }
    );
    res.json(updatePost);
  } catch (err) {
    res.json({ message: err });
  }
});

module.exports = router;

```

