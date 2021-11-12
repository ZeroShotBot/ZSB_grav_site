---
title: 'Contact Form'
cache_enable: false
body_classes: modular
form:
    name: kontakt-ajax-form
    template: form-messages
    action: /contact
    refresh_prevention: true
    fields:
        -
            name: name
            placeholder: ' '
            label: false
            autofocus: 'off'
            autocomplete: 'on'
            validate:
                required: 'true'
            type: text
        -
            name: email
            placeholder: ' '
            label: false
            validate:
                required: 'true'
            type: email
        -
            name: subject
            placeholder: ' '
            label: false
            type: text
        -
            name: message
            label: false
            placeholder: Message
            type: textarea
            validate:
                required: 'true'
            rows: 5
    buttons:
        -
            type: submit
            value: Submit
            outerclasses: form-field
            classes: 'vlt-btn vlt-btn--secondary vlt-btn--lg'
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to:
                    - '{{ config.plugins.email.from }}'
                    - '{{ form.value.email }}'
                subject: '[Message from] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            message: 'Thanks for your message! We''ll be in touch...'
---

