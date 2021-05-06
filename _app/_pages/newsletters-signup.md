---
layout: page
title: Newsletters
permalink: /newsletters/
desc: 電郵訂閱・ニュースレター・Newsletters
---

Sign up for the newsletter. You will get email updates when new posts are published.

<form action="//00ffff.us2.list-manage.com/subscribe/post?u=eef500b1fe3fe595f03a27605&amp;id=7bbabe95a9" method="post">
  <input name="EMAIL" type="email" placeholder="Your Email" required>
</form>

<button id="checkout-button-price_1IYR8oJsdPDBXd9EbPVcEBl7"
                role="link"
                type="button"
                class="button">tap here to subscribe</button>

<script>
(function() {
  var stripe = Stripe('pk_live_51IVCihJsdPDBXd9E9fCtHvT4Kn48cqELBrYPi3CsvJ7ywN1lTrgHvQ7NMypgoUVyicvjbhrSzm0HKvwl1rOjY5vW00wmrxYEtz');

  var checkoutButton = document.getElementById('checkout-button-price_1IYR8oJsdPDBXd9EbPVcEBl7');
  checkoutButton.addEventListener('click', function () {
    /*
     * When the customer clicks on the button, redirect
     * them to Checkout.
     */
    stripe.redirectToCheckout({
      lineItems: [{price: 'price_1IYR8oJsdPDBXd9EbPVcEBl7', quantity: 1}],
      mode: 'subscription',
      /*
       * Do not rely on the redirect to the successUrl for fulfilling
       * purchases, customers may not always reach the success_url after
       * a successful payment.
       * Instead use one of the strategies described in
       * https://stripe.com/docs/payments/checkout/fulfill-orders
       */
      successUrl: 'http://shadowportapp.surge.sh/success',
      cancelUrl: 'http://shadowportapp.surge.sh/canceled',
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
    stripe.createSource({
    type: 'wechat',
    amount: 4.99,
    currency: 'cad',
    }).then(function(result) {
      // handle result.error or result.source
    });
  });
})();
</script>