# Payments Example Gateway

Module implements fake payment gateway. It does not process any money. It should be used for testing purpose. You can simulate success or failed payment.
Name of the gateway: `example_gateway`

## Installation

        git clone git@github.com:Platform-OS/pos-module-payments-example-gateway.git modules/payments_example_gateway

## Usage

After you install module you can use `payments` module with `example_gateway` gateway type.

## Examples

Code examples

        {% liquid
          assign ids = '["1", "2"]' | parse_json
          assign object = null | hash_merge: gateway: 'example_gateway', payable_ids: ids, amount_cents: 1001, currency: 'USD'
          function object = 'modules/payments/commands/transactions/create', object: object
          echo object
          echo '------------------'

          function url = 'modules/payments/helpers/pay_url', transaction: object
          echo url
          echo '------------------'
        %}
        <a href="{{ url  }}">Pay</a>

## Versioning

```
git fetch origin --tags
npm version major | minor | patch
```
