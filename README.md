# PhantomPen: Face and Free-Hand Signature Authentication

PhantomPen is a **two-step biometric authentication system** that combines facial recognition with free-hand signature verification.

Users first verify their identity through facial recognition. After passing the face verification step, they draw their signature in the air using hand gestures captured by a webcam. The system then compares the newly drawn signature with the enrolled signature to determine whether authentication succeeds.

The project was originally developed at **TartanHacks 2025 at Carnegie Mellon University** and was later extended into a dual-verification system for the **5th Girls in Cyber Security (GiCS) Competition**, where it received **3rd Place**.

## Key Features

- Two-step biometric authentication using **facial recognition and signature verification**
- Real-time hand and finger tracking with computer vision
- Touch-free signature input using thumb-and-index-finger gestures
- AI-based signature similarity matching
- User authentication database for enrolled identities and signatures
- Interactive GUI for username input and authentication results
- Multiple signature visualization styles, including glow, neon blue, fire, and white

## How It Works

### 1. User Identification

The user enters their username through the authentication interface.

### 2. Facial Recognition

The webcam captures the user's face and compares it with the enrolled facial data.

- If face verification fails, authentication stops.
- If face verification succeeds, the user proceeds to signature verification.

### 3. Free-Hand Signature Input

The user draws their signature in the air in front of the webcam.

MediaPipe-based hand tracking detects the thumb and index finger. Bringing the two fingertips together starts drawing, while separating them stops the stroke.

### 4. Signature Verification

The captured signature is processed and compared with the user's enrolled signature using the trained signature verification model.

### 5. Authentication Result

Access is granted only after the required biometric verification steps succeed.

## Technical Pipeline

```text
Username Input
      |
      v
Facial Recognition
      |
      | verified
      v
Hand / Finger Tracking
      |
      v
Free-Hand Signature Capture
      |
      v
Signature Similarity Verification
      |
      v
Authentication Result
```

## Technologies

- Python
- OpenCV
- MediaPipe
- PyTorch
- NumPy
- Tkinter
- Computer Vision
- Siamese-network-based signature verification
- Facial recognition

## Installation

Python 3.10 is recommended.

```bash
conda create -n PhantomPen python=3.10
conda activate PhantomPen
pip install -r requirements.txt
```

The project was primarily tested on macOS. GUI or camera behavior may differ on Windows depending on the local environment.

## Signature Enrollment

To collect signature samples for a user:

```bash
python3 simple_draw.py --name <your_name> --style <style> -p
```

Available styles:

- `glow`
- `neon_blue`
- `fire`
- `white`

The `-p` flag enables the Phantom visual effect.

### Drawing Controls

- Touch the thumb and index fingertips together: start drawing
- Separate the fingertips: stop drawing
- Press `s`: save the signature
- Press `c`: clear the canvas
- Press `q`: quit

## Authentication

Run the complete authentication pipeline with:

```bash
python3 main.py --style <style> -p
```

The application will:

1. Ask for the username.
2. Perform facial verification.
3. Allow the user to draw a signature after successful facial verification.
4. Compare the captured signature with the enrolled signature.
5. Display the authentication result through the GUI.

## Competition Achievement

**3rd Place — 5th Girls in Cyber Security (GiCS) Competition**

The competition version extended PhantomPen from free-hand signature authentication into a multi-biometric verification system by integrating facial recognition with the signature authentication pipeline.

Project contributions included:

- Developing the free-hand signature verification pipeline using computer-vision-based finger tracking and AI-based identity matching
- Building and organizing the authentication database
- Integrating facial recognition with the user verification interface and signature authentication workflow

## Background

PhantomPen was first created for **TartanHacks 2025 at Carnegie Mellon University** as a touch-free signature authentication prototype. The system was subsequently expanded to improve identity verification through an additional facial-recognition stage and used in the GiCS competition.

## Developers & Contributors

See the repository contributors and commit history for individual contributions.
