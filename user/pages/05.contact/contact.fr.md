---
title: 'Nous contacter'
form:
    name: contact-form
    fields:
        -
            name: name
            label: Name
            placeholder: 'Enter your name'
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            classes: 'name form-control'
            validate:
                required: true
        -
            name: email
            label: Email
            placeholder: 'Enter your email address'
            type: email
            classes: 'mail form-control'
            validate:
                required: true
        -
            name: message
            label: Message
            classes: 'form-control form-control-lg'
            size: long
            placeholder: 'Enter your message'
            type: textarea
            validate:
                required: true
    buttons:
        -
            type: submit
            classes: 'btn btn-primary'
            value: Submit
        -
            type: reset
            classes: btn
            value: Reset
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ form.value.email }}']
                subject: '[Feedback] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: contact-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Merci pour votre avis!'
        -
            display: thankyou
---

Nous aimerions recevoir de vos nouvelles. Intéressé à travailler ensemble? Remplissez le formulaire ci-dessous avec quelques informations sur votre projet et je vous répondrai dès que possible. Permettez-moi quelques jours de répondre.
