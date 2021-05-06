---
layout: page
title: Newsletters
permalink: /newsletters/
desc: 電郵訂閱・ニュースレター・Newsletters
---

Sign up for the newsletter. You will get email updates when new posts are published.

<form>
  <input name="EMAIL" type="email" placeholder="Your Email" required>
</form>

<!-- Load Stripe.js on your website. -->
<script src="https://js.stripe.com/v3"></script>

<!-- Create a button that your customers click to complete their purchase. Customize the styling to suit your branding. -->
<button style="background-color:#6772E5;color:#FFF;padding:8px 12px;border:0;border-radius:4px;font-size:1em" id="checkout-button-price_1IlrMKBvZ7LmT93teJNEk6aQ" role="link" type="button">Checkout</button>

<div id="error-message"></div>

<script>
(function() {
  var stripe = Stripe('pk_live_51Ifl9MBvZ7LmT93tfkpybDhly6KAaEJuQWju16Kd50qvTE8xIQiQpmFbP1X5ow8sOiMpeW6q3xz0Gug8383ubY9h005suqpzL5');

  var checkoutButton = document.getElementById('checkout-button-price_1IlrMKBvZ7LmT93teJNEk6aQ');
  checkoutButton.addEventListener('click', function () {
    /*
     * When the customer clicks on the button, redirect
     * them to Checkout.
     */
    stripe.redirectToCheckout({
      lineItems: [{price: 'price_1IlrMKBvZ7LmT93teJNEk6aQ', quantity: 1}],
      mode: 'subscription',
      /*
       * Do not rely on the redirect to the successUrl for fulfilling
       * purchases, customers may not always reach the success_url after
       * a successful payment.
       * Instead use one of the strategies described in
       * https://stripe.com/docs/payments/checkout/fulfill-orders
       */
      successUrl: window.location.protocol + '//00ffff.com/success',
      cancelUrl: window.location.protocol + '//00ffff.com/canceled',
    })
    .then(function (result) {
      if (result.error) {
        /*
         * If `redirectToCheckout` fails due to a browser or network
         * error, display the localized error message to your customer.
         */
        var displayError = document.getElementById('error-message');
        displayError.textContent = result.error.message;
      }
    });
  });
})();
</script>