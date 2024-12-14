# YouTube Proxy Viewer

YouTube Proxy Viewer is a web application that allows users to watch YouTube videos anonymously, even in countries where YouTube is filtered. The app is built using Vue.js and Tailwind CSS and provides a user-friendly interface with space for advertisements.

## Features

- Enter a YouTube video URL to watch the video anonymously.
- Proxy support to bypass filtering in restricted regions.
- Responsive design with ad spaces on the sides.
- Footer with links to developer's LinkedIn and GitHub.

## Technologies Used

- **Vue.js**: For building the user interface.
- **Tailwind CSS**: For styling the application.
- **TypeScript**: For type-safe JavaScript.

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/Alireza-shahbaziyan/YouTube-Proxy-Viewer/
   ```

2. Navigate to the project directory:
   ```bash
   cd youtube-proxy-viewer
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Run the development server:
   ```bash
   npm run dev
   ```

5. Open your browser and navigate to `http://localhost:3000`.

## Deployment

To deploy the app:

1. Build the application:
   ```bash
   npm run build
   ```

2. Serve the built files using a static file server, or deploy to a hosting service like Netlify or Vercel.

## Backend Requirement

This application requires a backend service to act as a proxy for fetching YouTube videos. Make sure to replace `https://your-backend-domain.com/api/proxy` in the code with the URL of your backend service.

## Developer

This application was developed by [Your Name].

- **LinkedIn**: [Your LinkedIn Profile](https://www.linkedin.com/in/alireza-shahbaziyan-a4b187231/)
- **GitHub**: [Your GitHub Profile](https://github.com/Alireza-shahbaziyan)

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
