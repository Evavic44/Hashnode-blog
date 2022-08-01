## Spekni - A recognition platform built for developer endorsements

[Spekni](https://spekni.vercel.app) is a platform for recognizing developers making an impact, contributing to better open-source projects, helping other developers, creating quality tutorials, and writing helpful articles in the tech community for the sole purpose of getting them noticed by the right people. 

Spekni also works as a platform for finding capable developers because we simplify the process for recruiters to find passionate developers. We know most companies find it hard to find well-experienced developers who match the skills on their resumes. Endorsements from other experienced developers can go a long way in fixing that problem.

## Inspiration
Most developers do not seek credit for their work, tirelessly putting in a lot of effort to deliver great projects for users, clients, and other devs. Sometimes developers who constantly give back to the community are the least appreciated, and as such, they sometimes find it hard to get recognition for their work. This is what we hope to fix with Spekni 🎉

## UI/UX and Style Guide
We choose the color blue which signifies trust, peace, loyalty, and competence just like Hashnode. The design was done completely on Figma, and we drew inspirations from several websites like [Vercel](https://vercel.com), [Toptal](https://toptal.com), [Peerlist](https://peerlist.io), etc. Since this is a product for developers, we had to add a dark mode feature with system default theme switching. 😁

## How does Spekni Work?

### 📍 Login

To get started on Spekni, simply visit the login page, in this page, we've provided two sign-up mediums: GitHub and Google. This authentication is powered by [NextAuthJS](https://nextauth.io). 

![Spekni Login page](https://cdn.hashnode.com/res/hashnode/image/upload/v1658866880984/Gox6i4LUX.png align="left")

###  📍 Edit Account

After connecting your account, you'll be redirected to the edit account page, in this page users can fill up the form with their bio information, job description, social accounts, and finally, their stack/tech skills, 

![profile-page.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659333551677/4FATvs5HH.png align="left")

The skills in this section are set up in a way that they would be endorsable by another user that is fully registered and authenticated on the platform. For now, a user can have a minimum of 3 skills and a maximum of 6 skills which we might increase later. The skills input fields are limited to 40 characters because we expect keywords like **JavaScript, Public Speaking, Open source, NextJS, Technical Writing, C++, PHP, etc.** 

![skills-form.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659333659234/sBtQaIo9R.png align="left")

Though we are still working on making this more accessible to users, so if you have suggestions or ways we can improve on it, you can drop your [suggestions](https://forms.gle/MisTGbxSyw3Ji8hf7), and we might give you a shout-out in our changelogs if they are implemented. 😉

###  📍 Profile

Automatically all data provided in this form are stored on the PlanetScale database. A simple configuration of the database and code will allow these skills to be endorsable. Your profile is stored in your unique username which another user can visit to see your profile, for example, you can check out my profile: [https://spekni.com/eke](https://spekni.com/eke)

###  📍 Endorsements
Once you finish setting up your profile, you can now start getting your skills endorsed by other people who register on the platform. It's pretty straightforward.

![confetti.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1659336117990/k_1dCkEd3.gif align="left")

###  📍 Recommendation

Users can also drop recommendations to other developers by visiting their profile and adding what they will like to say about the developer in the input box. Here you can talk in-depth about someone's particular skill, past projects, or overall behavior. 

![recommendation.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659339226071/HTZ9Czn5f.png align="left")

## 📍 Explore 
The explore page is where all successfully registered members can be found. Once you set up your account, you are automatically added to this explore page. These users are stored in the PlanentScale database.

![explore.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659339477080/b0m5EQOue.png align="left")

Excited about this? Join [here](https://vercel.app/login) 🎉

## Tools used in building Spekni
Spekni is completely built with NextJS for the frontend and PlanetScale for the backend, and of course, PlanetScale was used for the database. Here's a short list of some of these tools:

- 🎯 [NextJS](https://nextjs.org) - Frontend
- 🌀 [NodeJS](Backend)
- ☑️ [Vercel](https://vercel.com) - Hosting and deployment
- 🔒 [NextAuth.js](https://nextauth.io): GitHub and Google Authentication 
- 📦 [PlanetScale](https://planetscale.io): Database Storage & API 
- 💅🏽 [TailwindCSS](https://tailwindcss.com) / CSS - Styling and UI
- 🗃️ [Prisma](https://prism.io): database schema design
- ☀️ [Next Themes](https://github.com/pacocoursey/next-themes): Color Theme
- 🎭 [Cloudinary](https://cloudinary.com) - Cloud media storage
- 🖼️ [Lazyload NPM package](https://lazyload.com): Image optimization
- ⚖️ [Mit License](https://github.com/evavic44/spekni/license) - Open source License


### Frontend

#### UI framework
We used NextJS for the frontend because of its speed and great analytics. This is my first time working with NextJS and I have to say, I'm quite impressed with the framework ecosystem. One of the key reasons we used NextJS was to harness its SEO power and automatic routing system, which helped us tremendously to make Spekni fast and have a great SEO.

Without the need of using a routing system like [react-router](https://react-router.com). Here's the folder structure of each of the pages on Spekni. Creating a file on this page automatically creates a route with the subdomain. Which is mind-blowing 🤯

Here's the folder structure of our pages directory:
```js
├── pages
│   ├── [username]
│   ├── 404
│   ├── about
│   ├── account
│   ├── API
│   │   ├── auth
│   │   ├── users
│   ├── explore
│   ├── login
│   ├── _app.js
│   ├── _document.js
│   ├── error.js
│   ├── index.js
│   ├── profile.js
```

#### TailwindCSS & NextJS module CSS
For the styling, we used TailwindCSS and their UI components from Headless UI to speed up the development of this project. In some cases where Tailwind was not reachable, we complimented with NextJS built-in `CSS` Modules which allowed us to use the same `CSS` class name in different files without worrying about collisions. The result of pairing these two resulted in smaller bundle size.

![build-size.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659332767817/lWP8eY-lx.png align="left")

### Backend
The backend for Spekni was built in NodeJS

## Role of PlanetScale
Plantescale is an excellent service for creating databases swiftly. We used PlanetScale to store user data of people signed up on the platform. Here's a screenshot of what the schema looks like

![database_diagram.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659324347996/3rqRmYSya.png align="left")

We used Prisma as an ORM(Object-relational mapping tool) for our database, we also leveraged Prisma's schema feature to define types for database tables and entities which we pushed to planetscale 

## Running spekni locally.

```bash
git clone https://github.com/Evavic44/spekni.git
cd src

npm install
npm run dev
```

Open `http://localhost:3000` with your browser to see the result.

## Challenges
Building Spekni was an amazing experience, but there were some challenges we had that I believe will be beneficial to explain how we solved them. 

### Prisma windows error
We had a few system compatibility issues with prisma. Spiff was on a linux machine while I am on windows. Running `prisma generate` wasn't working for me initially but it worked on Spiff's linux environment. 

```js
error - Error: @prisma/client did not initialize yet. Please run "Prisma generate" and try to import it again.
In case this error is unexpected for you, please report it at https://github.com/prisma/prisma/issues
```

```js
 Attempted to load @next/swc-win32-x64-msvc, but an error occurred: The specified module could not be found.
```

Prisma will not work because we need to install Microsoft VC++ redistributable packages on a Windows machine, you can install [here](https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170): 

Download both the x32 and x64 versions, after installing it, run:

```js
npx Prisma generate
```

## Additional Features and Summary
These are some of the features we weren't able to implement before launching Spekni. Though we are currently working on them so keep an eye out for the next release. 👀

- Endorsements Export: Users can add endorsements to their portfolio website through an `iframe`.
- Recruiters: Find a list of endorsed recruiters with a good track record of hiring the best developers.
- Explore Search: A feature for finding developers registered on the platform.

## Credits
It will be impossible to complete this project without giving proper credit to the persons that made this a success. After all, that's what Spekni is all about. In no particular order, here are the credits.

- [PlanetScale](https://planetscale.com) - For providing an excellent database service
- [Hashnode](https://hashnode.com) - For organizing this hackathon. 💙
- @[James Q Quick](@jamesqquick) - For support and answering our dumbest questions on Discord 😆
- @[Eleftheria Batsou](@eleftheriabatsou) - For her amazing feedback and reviews.

## Creators of Spekni
- [Victor Eke](https://github.com/evavic44) - Frontend & UI Lead
- [Spiff Jekey Green](https://github.com/spiffgreen) - Backend Lead
- [Nicholas Ovunda](https://github.com/nicholasovunda) - Backend and UI design

## Important Links
- [Live URL](https://spekni.vercel.app)
- [GitHub URL](https://github.com/evavic44/spekni)

This project was built for the [PlanetScale](https://planetscale.com) and [Hashnode](https://hashnode.com) Hackathon