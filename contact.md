---
layout: default
title: Contact
permalink: /contact/
---

<div class='container-fluid container-content'>
  <div class='row'>
    <div class='col-md-8 col-md-offset-2'>
      <div class='page-header'>
        <h2>
          <span class='fa fa-handshake-o'></span>
          Contact
        </h2>
      </div>
    </div>
    <div class='col-md-8 col-md-offset-2'>
      <form action='https://formspree.io/me@cameronstanley.com' method='POST' class='form-horizontal'>
        <div class='form-group'>
          <label for='name' class='col-sm-2 control-label'>Name</label>
          <div class='col-sm-8'>
            <input type='text' id='name' name='name' class='form-control' placeholder='Enter your name'>
          </div>
        </div>
        <div class='form-group'>
          <label for='email' class='col-sm-2 control-label'>Email</label>
          <div class='col-sm-8'>
            <input type="email" id='email' name="email" class='form-control' placeholder='Enter your email'>
          </div>
        </div>
        <div class='form-group'>
          <label for='email' class='col-sm-2 control-label'>Message</label>
          <div class='col-sm-8'>
            <textarea id='message' name='message' class='form-control' placeholder='Enter your message' rows='3'></textarea>
          </div>
        </div>
        <div class='form-group'>
          <div class='col-sm-offset-2 col-sm-8'>
            <input type="submit" class='btn btn-md btn-primary' value="Send">
          </div>
        </div>
      </form>
    </div>
  </div>
</div>
