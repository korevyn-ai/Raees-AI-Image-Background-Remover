# Erasely - AI Image Background Remover

Erasely is an AI-powered web application that helps users remove
backgrounds from images through a simple, user-friendly interface. Users
can create an account, log in, upload an image, preview the processed
result, and download the output image.

## Key Features

-   **User Authentication:** Sign up and log in using Supabase
    Authentication.
-   **Image Upload:** Upload JPG, PNG, and WEBP images, with a 10 MB
    upload limit configured in the application.
-   **AI Background Removal:** Uses Python and the `rembg` library to
    process images and remove their backgrounds.
-   **Image Preview:** Preview the processed image before downloading.
-   **Download Result:** Download the processed image as a PNG.
-   **Web Interface:** Built with React.js and CSS.
-   **Backend API:** Node.js and Express.js receive image uploads and
    coordinate the Python processing script.

## Technology Stack

  Technology                Purpose
  ------------------------- -----------------------------------------------
  React.js                  Frontend user interface
  JavaScript                Application logic
  CSS                       Layout and styling
  Node.js                   Backend runtime
  Express.js                HTTP server and API endpoints
  Python                    Image-processing script
  `rembg`                   AI-based background removal
  Supabase Authentication   User registration and login
  Vite                      Frontend development server and build tooling
  Git and GitHub            Version control and source-code hosting

## How It Works

1.  The user opens Erasely and signs up or logs in.
2.  The user selects an image to upload.
3.  The React frontend sends the image to the backend API.
4.  The Express server receives the image and starts the Python
    processing script.
5.  Python uses `rembg` to remove the background and generate the
    processed image.
6.  The backend returns the output image URL to the frontend.
7.  The user previews and downloads the result.

## Project Structure

``` text
Erasely/
├── backend/
│   ├── uploads/          # Input/output images handled by the backend
│   ├── server.js         # Express server and background-removal API
│   ├── remove_bg.py      # Python image-processing script
│   ├── package.json      # Backend Node.js dependencies and scripts
│   └── requirements.txt  # Python dependencies
├── public/               # Public static assets
├── src/
│   ├── assets/           # Frontend image assets
│   ├── App.jsx            # Main React component and application flow
│   ├── App.css            # Component styles
│   ├── index.css          # Global styles
│   ├── main.jsx           # React entry point
│   └── styles.css         # Additional styles
├── index.html
├── package.json           # Frontend dependencies and scripts
├── vite.config.js
└── README.md
```

*The exact files may vary slightly as the project evolves.*

## Requirements

-   Node.js and npm
-   Python
-   Python dependencies listed in `backend/requirements.txt`
-   A configured Supabase project for authentication
-   The `rembg` model and dependencies required by the Python script

## Run Locally

### 1. Clone the repository

``` bash
git clone https://github.com/korevyn-ai/Raees-AI-Image-Background-Remover.git
cd Raees-AI-Image-Background-Remover
```

### 2. Install frontend dependencies

From the project root:

``` bash
npm install
```

### 3. Install backend Node.js dependencies

``` bash
cd backend
npm install
```

### 4. Install Python dependencies

From the `backend` directory:

``` bash
pip install -r requirements.txt
```

Make sure the Python command and the required `rembg` model are
available in your environment.

### 5. Configure environment variables

Configure the Supabase project URL and publishable key in the frontend
using the variable names expected by the application. Configure any
backend environment variables required by your setup.

**Security:** Do not commit private keys, service-role keys, passwords,
or other secrets to GitHub. Use environment variables for sensitive
configuration.

### 6. Start the backend

From the `backend` directory, run the start command defined in
`backend/package.json`. For example, if the configured script is
`start`:

``` bash
npm start
```

The backend defaults to port `5000` when `PORT` is not set.

### 7. Start the frontend

Open another terminal at the project root and run:

``` bash
npm run dev
```

Open the local URL printed by Vite in the terminal.

> **Note:** Check the frontend API URL before running locally or
> deploying. The frontend and backend must point to the correct
> environment. The backend must be running for background removal to
> work.

## API Endpoint

### `POST /api/remove-background`

Accepts a multipart form upload with the file field named `image`.

-   **Input:** An image uploaded as the `image` form field.
-   **Successful response:** JSON containing `success`, `message`, and
    `outputUrl`.
-   **Possible errors:** Missing upload, failed image processing, or
    missing output file.

The exact response and behavior are defined by `backend/server.js`.

## Limitations

-   Processing time depends on the image, AI model, and available server
    resources.
-   Output quality may vary with image complexity, lighting, and subject
    edges.
-   Background removal requires the backend and Python processing
    environment to be available.
-   Only the image formats and file sizes configured by the application
    are supported.

## Future Enhancements

-   Improve processing speed and output quality.
-   Add background replacement and additional image-editing tools.
-   Add secure image history, if required.
-   Improve processing progress feedback and error messages.
-   Explore a mobile-friendly application experience.

## Contributors

-   **Raees Muktar Patel**
-   **Saad Imtiyaz Sayyad**

## Acknowledgements

This project was developed as an AI-based web application project. It
uses open-source technologies including React.js, Node.js, Express.js,
Python, and `rembg`.

## License

No license has been specified yet. Unless a license is added to this
repository, reuse and redistribution are subject to the applicable
copyright rules.
