---
layout: lesson
title: Connecting Client & Server
slides: ['_slides/week-03/04-connecting-client-server.md']
lesson_date: 2018-07-19
---

## Pre-Work

Prior to class, read through the following documentation:

- [Apollo Client Docs (Intro and Essentials sections)](https://www.apollographql.com/docs/react/)
- [React Docs on Forms](https://facebook.github.io/react/docs/forms.html)

---

## Learning Objectives

- Install and Apollo Client in a project and use it to make queries to a GraphQL API that populate data in React components.
- Describe UX best practices for implementing client-side validation.
- Provide error feedback on invalid input.
- Distinguish between controlled and uncontrolled components.
- Use a library for handling form validation and submission in an application.
- Use form components from third-party libraries including React Final Form and Material UI.
- Use Apollo Client to request mutations from the client side of an application via a form.

---

## Keywords

- Controlled component
- Uncontrolled component
- Client-side validation

---

## Exercise 1

Write a basic form in HTML that alerts the value of an input.

---

## Exercise 2

Install a repo of React-Form demos.

```shell
git clone https://github.com/redacademy/adp-react-forms.git
cd adp-react-form-demos
npm install
npm start
```

---

## Exercise 3

Add an extra field to either your **controlled** or **uncontrolled** form.

The output data should be in JSON, like the following:

```json
{
  "username": "name",
  "password": "pass"
}
```

---

## Exercise 4

Add any of the following to a form of your choosing:

- Show an error message if the password is shorter than 5 characters
- Make it impossible for a user to type a username longer than 8 characters
- Validate that a username does not contain any capital letters
- Disable the submit button if any of the fields are invalid

---

## Lab Activity

Create the forms that you'll use in your Boomtown app, using the [React Final Form](https://github.com/final-form/react-final-form) library.
You'll need to create both a user (login) form and a form for adding new Items.

Be sure to include:

- Validation of fields
- Styled components
- Error feedback

---

## Additional Resources

- [Material UI](https://github.com/callemall/material-ui)
- [Semantic UI](http://react.semantic-ui.com/)