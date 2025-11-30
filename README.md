<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Feedback Form</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .feedback-box {
      background: #fff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      text-align: center;
      width: 320px;
    }
    .stars {
      margin: 15px 0;
      /* Using font-weight: bold makes the &#9733; entity look solid */
      font-weight: bold; 
    }
    .stars span {
      font-size: 32px;
      cursor: pointer;
      /* Initial star color (gray) */
      color: #ccc; 
      transition: color 0.3s;
    }
    .stars span.active {
      /* Selected star color (gold) */
      color: #ffb400; 
    }
    textarea {
      width: 100%;
      height: 80px;
      margin-top: 10px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ddd;
      resize: none;
    }
    button {
      margin-top: 15px;
      padding: 10px 20px;
      background: #0078d7;
      color: #fff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: #005fa3;
    }
  </style>
</head>
<body>
  <div class="feedback-box">
    <h2>Rate Us</h2>
    <div class="stars">
      <span data-value="1">&#9733;</span>
      <span data-value="2">&#9733;</span>
      <span data-value="3">&#9733;</span>
      <span data-value="4">&#9733;</span>
      <span data-value="5">&#9733;</span>
    </div>
    <textarea id="comment" placeholder="Optional feedback..."></textarea>
    <button onclick="submitFeedback()">Submit</button>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
  <script>
    let rating = 0;
    const stars = document.querySelectorAll('.stars span');

    stars.forEach(star => {
      star.addEventListener('click', () => {
        // Get the rating as an integer
        const clickedRating = parseInt(star.getAttribute('data-value'));
        rating = clickedRating; 

        // Clear all active classes
        stars.forEach(s => s.classList.remove('active'));

        // Add active class up to the clicked rating index
        for (let i = 0; i < clickedRating; i++) {
          stars[i].classList.add('active');
        }
      });
    });

    function submitFeedback() {
      const comment = document.getElementById("comment").value;
      Swal.fire({
        title: 'Thank you!',
        html: `<p>You rated <b>${rating} stars</b></p>
               <p>${comment ? "Your comment: " + comment : "No comment provided."}</p>`,
        icon: 'success',
        showConfirmButton: false,
        timer: 2500,
        backdrop: true
      });
    }
  </script>
</body>
</html># qrcode
