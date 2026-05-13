### Backend 
1. Generate package.json
2. Create .env file
3. Create express app & assign port number
4. Connect to db
5. Define schemas and create Models
    -- UserTypeSchema
        firstName
        lastName
        email(unique)
        password
        role
        profileImageUrl
        isUserActive
    -- ArticleSchema
        author
        title
        category
        content
        comments
        isArticleActive
6. Implement APIs
7. Create common api for register, login and logout
### Frontend
    Dynamic, Responsive User Interfaces(UI== web page--->Browser)
                               HTML
                  CSS(styles & Responsiveness)  , Bootstrap, TailwindCSS    
    JavaScript
    ReactJS/Angular/Vue/NextJS       

- Install cloudinary & multer
        npm install cloudinary multer

cloudinary.js
-------------
import { v2 as cloudinary } from "cloudinary";

cloudinary.config({
  cloud_name: process.env.CLOUD_NAME,
  api_key: process.env.API_KEY,
  api_secret: process.env.API_SECRET,
});

export default cloudinary;

cloudinaryUpload.js
-------------------
import cloudinary from "./cloudinary.js";

export const uploadToCloudinary = (buffer) => {
  return new Promise((resolve, reject) => {
    const stream = cloudinary.uploader.upload_stream({ folder: "blog_users" }, (err, result) => {
      if (err) return reject(err);
      resolve(result);
    });
    stream.end(buffer);
  });
};


# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

