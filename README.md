

https://github.com/user-attachments/assets/2bc3bf81-863e-4a73-a5fa-840e9741a0ad


                
  <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Veneer AI — Premium Brand Strategist</title>
<style>
  :root {
    --stone: #a79884;
    --charcoal: #2c2b28;
    --cream: #fbf7ef;
    --sage: #c3c1b7;
    --storm: #1d1b1a;
    --text-light: #f6f2ed;
    --soft-shadow: 0 20px 45px rgba(28, 24, 20, 0.2);
    font-family: 'Inter', system-ui, -apple-system, sans-serif;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    background: linear-gradient(180deg, #111010 0%, #1f1c1a 60%, #0f0d0c 100%);
    color: var(--text-light);
    min-height: 100vh;
  }
  .page { padding: 3rem 0 4rem; max-width: 1200px; margin: 0 auto; }
  header { padding: 0 1.5rem; display: flex; flex-direction: column; gap: 1rem; margin-bottom: 3rem; }
  header h1 { font-size: clamp(2.6rem, 4vw, 3.6rem); line-height: 1.15; margin: 0; letter-spacing: -0.02em; }
  
  /* Video Hero Styling */
  .hero-card {
    position: relative;
    min-height: 450px;
    border-radius: 24px;
    background: var(--storm);
    border: 1px solid rgba(255,255,255,0.1);
    overflow: hidden;
    margin: 0 1.5rem 3rem;
  }
  .hero-video {
    position: absolute;
    top: 50%; left: 50%;
    min-width: 100%; min-height: 100%;
    width: auto; height: auto;
    transform: translate(-50%, -50%);
    object-fit: cover;
    opacity: 0.6;
  }
  .video-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to bottom, transparent, var(--storm));
    z-index: 1;
  }

  .grid { display: grid; gap: 2rem; padding: 0 1.5rem; }
  .split { grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); }
  .card {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 20px;
    padding: 2rem;
    position: relative;
  }
  .badge {
    display: inline-flex; padding: 0.35rem 0.7rem;
    background: rgba(255,255,255,0.1); border-radius: 999px; font-size: 0.85rem;
  }
  form { display: flex; flex-direction: column; gap: 1rem; }
  input, textarea {
    border-radius: 12px; border: 1px solid rgba(255,255,255,0.2);
    background: rgba(255,255,255,0.03); padding: 0.9rem 1rem; color: #fff;
  }
  .primary-btn {
    padding: 1rem 1.4rem; border: none; border-radius: 999px;
    background: linear-gradient(135deg, var(--stone), var(--sage));
    color: var(--storm); font-weight: 600; cursor: pointer;
  }
  .success {
    margin-top: 1.5rem; padding: 1.5rem; border-radius: 16px;
    background: rgba(167, 152, 132, 0.15); border: 1px solid var(--stone);
    display: none; flex-direction: column; gap: 1rem; text-align: center;
  }
  .success.show { display: flex; }
  .payment-btn {
    background: #fff; color: #000; padding: 1rem;
    text-decoration: none; border-radius: 999px; font-weight: 700;
  }
</style>
</head>
<body>
  <div class="page">
    <header>
      <p class="badge">Lead Brand Strategist · Veneer AI</p>
      <h1>Transform raw e-commerce ideas into high-trust brands.</h1>
    </header>

    <div class="hero-card">
      <video autoplay muted loop playsinline class="hero-video">
        <source src="hero-video.mp4" type="video/mp4">
      </video>
      <div class="video-overlay"></div>
    </div>

    <section class="grid split">
      <div class="card">
        <h3>Submit Your Brief</h3>
        <form id="identity-form">
          <input type="text" name="brand" required placeholder="Brand / Client Name" />
          <textarea name="niche" rows="4" required placeholder="Describe the niche and mood"></textarea>
          <input type="email" name="email" required placeholder="Your Email" />
          <button type="submit" class="primary-btn">Submit for Identity Sprint</button>
          
          <div class="success" id="successMessage">
            <h3>Brief Received!</h3>
            <p>To finalize your 24-hour Brand Sprint, complete the secure payment below.</p>
            <a id="paymentLink" class="payment-btn" href="#">Pay $49 & Start Sprint</a>
          </div>
        </form>
      </div>
      
      <div class="card">
        <h3>Phase 1 Output</h3>
        <p>Your strategic partner workflow delivers a deconstructed audience profile, mission statement, and premium name options within 24 hours.</p>
      </div>
    </section>
  </div>

<script>
  // STEP 1: Paste your Zapier Webhook URL between the quotes below
  const ZAPIER_WEBHOOK_URL = 'PASTE_YOUR_LINK_HERE';

  // STEP 2: Paste your PayPal.me/Checkout link between the quotes below
  const PAYMENT_URL = 'PASTE_YOUR_PAYMENT_LINK_HERE';

  const form = document.getElementById('identity-form');
  const success = document.getElementById('successMessage');
  const paymentLink = document.getElementById('paymentLink');
  const submitBtn = form.querySelector('button[type="submit"]');

  paymentLink.href = PAYMENT_URL;https://paypal.me/Veenerai

  form.addEventListener('submit', async (event) => {
    event.preventDefault();
    const formData = new FormData(form);
    const data = Object.fromEntries(formData.entries());

    submitBtn.textContent = 'Processing...';
    submitBtn.disabled = true;

    try {
      await fetch(ZAPIER_WEBHOOK_URL, {https://hooks.zapier.com/hooks/catch/27252636/ujtjcu5/
        method: 'POST',
        mode: 'no-cors',
        body: JSON.stringify(data),
        headers: { 'Content-Type': 'application/json' }
      });

      // Backup local storage
      const leads = JSON.parse(localStorage.getItem('veneer_leads') || '[]');
      leads.push({ ...data, createdAt: new Date().toISOString() });
      localStorage.setItem('veneer_leads', JSON.stringify(leads));

      success.classList.add('show');
      submitBtn.textContent = 'Brief Sent';
    } catch (error) {
      submitBtn.textContent = 'Error. Try again?';
      submitBtn.disabled = false;
    }
  });
</script>
</body>
</html>    
