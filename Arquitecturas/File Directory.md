
[A post by _Daniel Moka_ on Linkedln](https://www.linkedin.com/posts/danielmoka_if-you-look-at-your-application-and-you-only-activity-7243514747634040832--XUN)

If you look at your application and you only see folders like these:

❌
📁 App

|__ 📁API

|__ 📁Models

|__ 📁Views

|__ 📁Controllers

|__ 📁DTOs

|__ 📁Database

|__ ...


- Then your app doesn't tell anything about the problem it solves. It's driven by technology instead of the domain. 🤖

- If you want to add a new feature, you need to add files to all these places. 😵

- Features are mixed, leading to maintenance hell. 🔥

Now look at this folder structure:

✅
📁 CarRentalService

|__ 📁AutoPicker

|__ 📁UserManager

|__ 📁PaymentGateway

|__ 📁InvoiceGenerator

|__ 📁SupportCenter

|__ ...

👉 It is called __screaming architecture__. __It screams the domain.__

## Points

- It is easy to navigate, with clear domain separations. 📁✔️

- If you want to add a new feature, you just add a new main directory. 🥰

- It has better discoverability and results in a low entry curve for new developers. 👶

> 💡 A clean folder structure is like a well-organized room; everything has its place, and it's easy to find what you need.

<img src="https://github.com/user-attachments/assets/354f35d9-f40e-4c6a-b502-09f9b07d2d65" height="300" />


☝️ Your folder structure __should communicate the domain__, __not the technology.__
