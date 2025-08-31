---
layout: page
permalink: /message-board/index.html
title: Message Board
---

<div class="content-section">
  <div class="left-spacer"></div>
  <div class="container" style="margin: 0 auto !important;">
    <section class="message-board-intro">
      <h1>Message Board</h1>
      <p>Welcome to my message board! Feel free to leave your thoughts, questions, or comments about my research and projects.</p>
    </section>

    <section class="message-board-content">
      <div class="message-form">
        <h2>Leave a Message</h2>
        <form class="contact-form" action="https://formspree.io/f/xpzgwqjq" method="POST">
          <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
          </div>
          
          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
          </div>
          
          <div class="form-group">
            <label for="subject">Subject:</label>
            <input type="text" id="subject" name="subject" required>
          </div>
          
          <div class="form-group">
            <label for="message">Message:</label>
            <textarea id="message" name="message" rows="6" required></textarea>
          </div>
          
          <button type="submit" class="submit-btn">Send Message</button>
        </form>
        
        <div id="form-success" class="form-message success" style="display: none;">
          <p>Thank you for your message! I'll get back to you soon.</p>
        </div>
        
        <div id="form-error" class="form-message error" style="display: none;">
          <p>Sorry, there was an error sending your message. Please try again or contact me directly via email.</p>
        </div>
      </div>

      <div class="contact-info">
        <h2>Other Ways to Connect</h2>
        <div class="contact-methods">
          <div class="contact-method">
            <h3>Email</h3>
            <p><a href="mailto:tiancheng.li@uts.edu.au">tiancheng.li@uts.edu.au</a></p>
          </div>
          
          <div class="contact-method">
            <h3>LinkedIn</h3>
            <p><a href="https://linkedin.com/in/tiancheng-li-robotics" target="_blank">Connect on LinkedIn</a></p>
          </div>
          
          <div class="contact-method">
            <h3>Google Scholar</h3>
            <p><a href="https://scholar.google.com/citations?user=BA8TUoAAAAAJ&hl=en" target="_blank">View Profile</a></p>
          </div>
        </div>
      </div>
    </section>
  </div>
  <div class="right-spacer"></div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const form = document.querySelector('.contact-form');
  const successMessage = document.getElementById('form-success');
  const errorMessage = document.getElementById('form-error');
  
  if (form) {
    form.addEventListener('submit', function(e) {
      // Hide any existing messages
      successMessage.style.display = 'none';
      errorMessage.style.display = 'none';
      
      // Show loading state
      const submitBtn = form.querySelector('.submit-btn');
      const originalText = submitBtn.textContent;
      submitBtn.textContent = 'Sending...';
      submitBtn.disabled = true;
      
      // For Netlify Forms, the form will be handled automatically
      // For Formspree, you might want to handle the response
      
      // Reset button after a delay (Netlify will handle the redirect)
      setTimeout(function() {
        submitBtn.textContent = originalText;
        submitBtn.disabled = false;
      }, 3000);
    });
  }
  
  // Check for success/error parameters in URL (for Formspree)
  const urlParams = new URLSearchParams(window.location.search);
  if (urlParams.get('success') === 'true') {
    successMessage.style.display = 'block';
  } else if (urlParams.get('error') === 'true') {
    errorMessage.style.display = 'block';
  }
});
</script>
