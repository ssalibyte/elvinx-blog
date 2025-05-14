import React from 'react';
import { BrowserRouter as Router, Routes, Route, Navigate } from 'react-router-dom';
import Home from './pages/Home';
import Blog from './pages/Blog';
import Login from './pages/Login';
import PostDetails from './pages/PostDetails';
import Navbar from './components/Navbar';
import Sidebar from './components/Sidebar';
import './App.css';

function App() {
  const user = true; // Simulated auth logic

  return (
    <Router>
      <div className="app-layout">
        <Sidebar />
        <div className="main-content">
          <Navbar />
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/login" element={<Login />} />
            <Route path="/blog" element={user ? <Blog /> : <Navigate to="/login" />} />
            <Route path="/blog/:id" element={<PostDetails />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}
export default App;

// === components/Navbar.js ===
import React from 'react';
import './Navbar.css';

const Navbar = () => {
  return (
    <nav className="navbar">
      <h1>ELVINX Blog</h1>
    </nav>
  );
};
export default Navbar;

// === components/Sidebar.js ===
import React from 'react';
import { Link } from 'react-router-dom';
import './Sidebar.css';

const Sidebar = () => {
  return (
    <aside className="sidebar">
      <h2 className="sidebar-title">ELVINX</h2>
      <ul>
        <li><Link to="/profile">Profile</Link></li>
        <li><Link to="/settings">Settings</Link></li>
        <li><Link to="/friends">Friends</Link></li>
        <li><Link to="/chat">Chat</Link></li>
      </ul>
    </aside>
  );
};
export default Sidebar;

// === pages/Home.js ===
import React from 'react';
import './Home.css';

const Home = () => {
  return (
    <div className="home">
      <h1 className="welcome">Welcome to <span className="brand">ELVINX</span></h1>
    </div>
  );
};
export default Home;

// === pages/Blog.js ===
import React from 'react';
import { Link } from 'react-router-dom';
import './Blog.css';

const posts = [
  { id: 1, title: 'My First Blog', content: 'Hello ELVINX readers!' },
  { id: 2, title: 'Update Notes', content: 'This update adds lots of features.' }
];

const Blog = () => {
  return (
    <div className="blog">
      <h2>Blog Posts</h2>
      {posts.map(post => (
        <div className="post" key={post.id}>
          <h3>{post.title}</h3>
          <p>{post.content}</p>
          <Link to={`/blog/${post.id}`}><button>Read more</button></Link>
        </div>
      ))}
    </div>
  );
};
export default Blog;

// === pages/PostDetails.js ===
import React from 'react';
import { useParams } from 'react-router-dom';

const PostDetails = () => {
  const { id } = useParams();
  return (
    <div style={{ padding: 20 }}>
      <h2>Post ID: {id}</h2>
      <p>Full blog content goes here...</p>
    </div>
  );
};
export default PostDetails;

// === pages/Login.js ===
import React from 'react';

const Login = () => {
  return (
    <div style={{ padding: 40 }}>
      <h2>Login Page</h2>
      <p>Login functionality placeholder</p>
    </div>
  );
};
export default Login;

// === App.css ===
.app-layout {
  display: flex;
  height: 100vh;
  font-family: 'Comic Sans MS', cursive;
  background-color: #f0f0f0;
}
.main-content {
  flex: 1;
  overflow-y: auto;
}

// === Sidebar.css ===
.sidebar {
  width: 200px;
  background: #ccc;
  padding: 20px;
  font-family: 'Comic Sans MS', cursive;
}
.sidebar-title {
  color: gray;
  font-size: 24px;
  font-style: italic;
  animation: fadeIn 1.5s ease;
}
ul {
  list-style: none;
  padding: 0;
}
ul li {
  margin: 10px 0;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

// === Navbar.css ===
.navbar {
  background: #444;
  padding: 10px;
  color: white;
  font-family: 'Comic Sans MS', cursive;
}

// === Home.css ===
.home {
  padding: 40px;
  text-align: center;
  background: linear-gradient(135deg, white, #eee);
}
.welcome {
  font-size: 36px;
  color: green;
  animation: slideIn 1.5s ease;
}
.brand {
  color: gray;
  font-style: italic;
}

@keyframes slideIn {
  from { opacity: 0; transform: translateX(-50px); }
  to { opacity: 1; transform: translateX(0); }
}

// === Blog.css ===
.blog {
  padding: 30px;
  background: white;
}
.post {
  margin-bottom: 20px;
  padding: 15px;
  border-radius: 10px;
  background: #fafafa;
  border: 1px solid #ddd;
  box-shadow: 2px 2px import React from 'react';
import { BrowserRouter as Router, Route, Routes, Navigate } from 'react-router-dom';
import Home from './pages/Home';
import Blog from './pages/Blog';
import Login from './pages/Login';
import PostDetails from './pages/PostDetails';
import Navbar from './components/Navbar';
import Sidebar from './components/Sidebar';
import './App.css';

function App() {
  const user = true; // Replace with actual auth logic

  return (
    <Router>
      <div className="app-container">
        <Sidebar />
        <div className="main-content">
          <Navbar />
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/login" element={<Login />} />
            <Route path="/blog" element={user ? <Blog /> : <Navigate to="/login" />} />
            <Route path="/blog/:id" element={user ? <PostDetails /> : <Navigate to="/login" />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}

export default App;

// components/Navbar.js
import React from 'react';
import './Navbar.css';

const Navbar = () => {
  return (
    <nav className="navbar">
      <h1 className="navbar-title">ELVINX Blog</h1>
    </nav>
  );
};

export default Navbar;

// Navbar.css
.navbar {
  background: #444;
  padding: 10px 20px;
  color: white;
  font-family: 'Comic Sans MS', cursive;
}

.navbar-title {
  margin: 0;
  font-size: 24px;
}

// components/Sidebar.js
import React from 'react';
import { Link } from 'react-router-dom';
import './Sidebar.css';

const Sidebar = () => {
  return (
    <div className="sidebar">
      <h2 className="sidebar-title">ELVINX</h2>
      <ul className="sidebar-menu">
        <li><Link to="/profile">Profile</Link></li>
        <li><Link to="/settings">Settings</Link></li>
        <li><Link to="/friends">Friends</Link></li>
        <li><Link to="/chat">Chat</Link></li>
      </ul>
    </div>
  );
};

export default Sidebar;

// Sidebar.css
.sidebar {
  width: 200px;
  background-color: #ccc;
  padding: 20px;
  font-family: 'Comic Sans MS', cursive;
  height: 100vh;
}

.sidebar-title {
  font-size: 24px;
  color: gray;
  font-style: italic;
  text-align: center;
  animation: fadeIn 2s ease;
}

.sidebar-menu {
  list-style: none;
  padding: 0;
}

.sidebar-menu li {
  margin: 15px 0;
}

.sidebar-menu a {
  text-decoration: none;
  color: black;
  font-weight: bold;
}

@keyframes fadeIn {
  0% { opacity: 0; transform: translateY(-20px); }
  100% { opacity: 1; transform: translateY(0); }
}

// pages/Home.js
import React from 'react';
import './Home.css';

const Home = () => {
  return (
    <div className="home-page">
      <h1 className="welcome-text">Welcome to <span className="elvinx">ELVINX</span></h1>
    </div>
  );
};

export default Home;

// Home.css
.home-page {
  padding: 40px;
  font-family: 'Comic Sans MS', cursive;
  background: linear-gradient(135deg, #ffffff, #eeeeee);
  text-align: center;
}

.welcome-text {
  font-size: 40px;
  color: green;
  animation: slideIn 2s ease-out;
}

.elvinx {
  font-style: italic;
  color: gray;
}

@keyframes slideIn {
  0% { opacity: 0; transform: translateX(-50px); }
  100% { opacity: 1; transform: translateX(0); }
}

// pages/Blog.js
import React from 'react';
import { Link } from 'react-router-dom';
import './Blog.css';

const dummyPosts = [
  { id: 1, title: 'First Post', content: 'This is your first blog post!' },
  { id: 2, title: 'Another Post', content: 'Here’s another interesting article.' }
];

const Blog = () => {
  return (
    <div className="blog-page">
      <h2>Blog Posts</h2>
      {dummyPosts.map(post => (
        <div className="post-card" key={post.id}>
          <h3>{post.title}</h3>
          <p>{post.content}</p>
          <Link to={`/blog/${post.id}`}><button>Read more</button></Link>
        </div>
      ))}
    </div>
  );
};

export default Blog;

// Blog.css
.blog-page {
  padding: 30px;
  font-family: 'Comic Sans MS', cursive;
  background-color: #f7f7f7;
}

.post-card {
  border: 1px solid #ddd;
  padding: 20px;
  margin: 15px 0;
  border-radius: 10px;
  background-color: white;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
}

// pages/Login.js
import React from 'react';

const Login = () => {
  return (
    <div style={{ padding: 40 }}>
      <h2>Login Page</h2>
      <p>This is a placeholder login screen.</p>
    </div>
  );
};

export default Login;

// pages/PostDetails.js
import React from 'react';
import { useParams } from 'react-router-dom';

const PostDetails = () => {
  const { id } = useParams();
  return (
    <div style={{ padding: 40 }}>
      <h2>Post Details - ID: {id}</h2>
      <p>Post content and comments would appear here.</p>
    </div>
  );
};
