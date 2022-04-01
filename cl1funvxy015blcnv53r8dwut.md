## Rocketmeme - A Meme Library and Editor for creating and sharing memes

## What is Rocketmeme 
[Rocketmeme](https://rocketmeme.com) is a simple and easy-to-use library and meme editor built with React and [Hasura GraphQL](https://hasura.io/) for creating, sharing, viewing, and downloading memes on the fly. Building Rocketmeme has been an amazing experience filled with learning new things and fixing bugs. This project was built by me and my good friend [Spiff Jekey Green](https://github.com/SpiffGreen): an amazing backend developer who tirelessly contributed to bringing this idea to fruition. 

## Inspiration 
Memes have become a part of our everyday interaction with one another, you see them shared in videos, social media, <a href="https://jswift.hashnode.dev/the-best-vs-code-extensions-to-supercharge-git-yes-theres-more-than-gitlens#ckqu277t702c2g9s14aw77uzt">articles</a>, and websites like [daily.dev](https://daily.dev/).

![daily.dev.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648707869918/6FAWyY8k2.jpg)

Statistics have shown that humor is a great way to draw people's attention or even cause interaction between people, and that is what memes are all about. Don't believe us? Check out Elon Musk on Twitter. :)

%[https://twitter.com/elonmusk/status/1276418907968925696?s=20&t=Q_WCV6A5Kc7JxlnHniGQnw]

Nah, he's kidding. 😅

## UI & Style Guide
Now we got the inspiration and knew what we plan on building, the next step was designing what it would look like. For the UI, we drew inspiration from [Unsplash](https://unsplash.com) and for the style guide, I did a google search for ideas and saw a cool [template](https://www.figma.com/community/file/898121305391200697) on Figma. I quickly stole, sorry forked the template, and updated the styles accordingly. :)

![rocketmeme-style-guide.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647790833299/F0Liv3HpA.png)

### Project Setup
We used GitHub automated [Kanban board](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards) to list out the major features for Rocketmeme and assigned a priority label to each issue to mark their level of importance. A major feature like [setting up Rocketmeme API with Hasura GraphQL](https://github.com/Evavic44/rocketmeme/issues/27) will take top priority and thus label would be marked: **Priority: High**

![project-board.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648392202330/jJjQuL6c9.png)

## Tech Stack 
Rocketmeme is completely built with React for the frontend and [Hasura](https://hasura.io/) for the backend. Below is a small list of libraries and tech stacks used to make this app what it is.

- [React](https://reactjs.org)
- [React Redux](https://react-redux.js.org/)
- [Styled Components](https://styled-components.com/)
- [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [Hasura GraphQL](https://hasura.io/)
- [Clerk](https://clerk.dev)
- [ImageKit](https://imagekit.io/)
- [Netlify](https://www.netlify.com/) 

## Features 
This app started as a simple meme editor but has gradually morphed into a library of memes with an API. Here are some of the core features of Rocketmeme:

### 1. Meme search
![rocketmeme-search-2.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1648724937451/QsF52AULG.webp)

Rocketmeme features a simple search bar on the homepage that allows users to browse through memes based on different categories like JavaScript, NFT, stackoverflow, ETC. At the time of writing this article, we've only added a few memes to the API so the results might be few for now. 

The meme search is powered by Hasura and fully paginated to avoid too many requests at once. By default, the search is set to search by category but it can be configured to search by id, title, and more.

```css
const getPaginatedMemeSearch = gql`
	query getPaginatedMemeSearch($searchTerm: String!) {
		memes(limit: 10, offset: 0, where: { category: { _ilike: $searchTerm } }) {
			id
			downloads
			likes
			views
			image_link
			category
			title
		}
	}
`;
```

### 2. Meme Editor
The meme editor is powered by [Interact JS](https://interactjs.io/), a powerful JavaScript drag & drop multi-touch library for creating editable fields with text and inputs. With the editor, users can edit a meme using a collection of high-quality images. 

![rocketmeme-editor.webp](https://cdn.hashnode.com/res/hashnode/image/upload/v1648750443738/BtFWP41xL.webp)

To create a meme, select from the meme templates on the top, which are lazy-loaded using [react-lazy-loader](https://re) to save the user's data and increase load time. After selecting the meme, click the "add text" button to start making the meme. The text can be resized or repositioned around the canvas.

You can also add icons and images from the image list or upload your preferred image from your device. To do this, click the "Add image" button, which will pop up a simple modal of icons, select your preferred image, and once added, you can resize or reposition the image around the canvas.

![rocketmeme-upload-image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1647893116022/lTb3d2kTy.png)

### 3. Meme API
```css
https://rocketmeme-user.hasura.app/v1/graphql
```

With Hasura, we were able to create a serverless API using [Hasura cloud](https://cloud.hasura.io). The API exists for two types of requests: The meme template and the uploaded memes which are handled by Hasura. If you're interested, you can start exploring the [API docs](https://victor-eke.gitbook.io/rocketmeme-api/) to get an idea of everything possible with the rocketmeme API.💛 

Here is an example snippet of the API exported by Hasura - if you plan on using it, you should consider tailoring it to your service.

```js
async function fetchGraphQL(operationsDoc, operationName, variables) {
  const result = await fetch(
    "undefined",
    {
      method: "POST",
      body: JSON.stringify({
        query: operationsDoc,
        variables: variables,
        operationName: operationName
      })
    }
  );

  return await result.json();
}

const operationsDoc = `
  query MyQuery {
    meme_templates(order_by: {id: asc, image_link: asc, title: asc}) {
      id
      image_link
      title
    }
  }
`;

function fetchMyQuery() {
  return fetchGraphQL(
    operationsDoc,
    "MyQuery",
    {}
  );
}

async function startFetchMyQuery() {
  const { errors, data } = await fetchMyQuery();

  if (errors) {
    // handle those errors like a pro
    console.error(errors);
  }

  // do something great with this precious data
  console.log(data);
}

startFetchMyQuery();
```

A typical response from the API looks something like this. 

```js
{
  "data": {
    "meme_templates": [
      {
        "id": 13,
        "image_link": "https://ik.imagekit.io/eke/meme-template/6a9d61_Ymb7HBcvJ.png?ik-sdk-version=javascript-1.4.3&updatedAt=1648578651816",
        "title": "Will Punching Chris"
      },
      {
        "id": 4,
        "image_link": "https://ik.imagekit.io/eke/meme-template/temp1_0nO6rB9BNK.png?ik-sdk-version=javascript-1.4.3&updatedAt=1648026808159",
        "title": "X, X Everywhere"
      }
    ]
  }
}
```

### 4. Login 
Creating an account in Rocketmeme can give you features like saving your edited memes, connecting your social accounts to easily share memes on your favorite social platform, upvoting or downvoting a meme, and more. For now, the login feature is disabled until we set up the user endpoint in Hasura, which will allow users that are logged in to upload memes they created. :)

## Challenges 
I'll say this has been the most challenging project I've worked on, so far and I wouldn't have been able to build this without the help of my good friend [Spiff](https://github.com/SpiffGreen). I learned a lot by collaborating with him and this will not be our last project together.

### Grid gallery
Rocketmeme features an awesome-looking grid layout for the uploaded memes on the homepage. This is being controlled by the **column-count** property. The CSS property I discovered was not done by any library because we wanted the application to be fast and most of the grid gallery libraries available were either on vanilla JS or jQuery. Building this gallery was very tough as some contents overlapped on each other when we first tested it. What we did was calculate the total width of the container and divide it into 3 parts where each part will occupy an image. We used the closest whole number 33% for each. This equally divided the containers and the size was perfect. 

### Dynamic image resizing
It is no surprise that I would require a way to dynamically serve Rocketmeme images based on different devices. This is to ensure images remain at the smallest size and with the best quality possible. I struggled with a way to do this until I discovered [Don't serve unoptimized images](https://m.youtube.com/watch?v=pfHG6HL1GBw&t=502s) by @[James Q Quick](@jamesqquick). In this tutorial, he utilized a service called [ImageKit](https://imagekit.io/) for optimizing images dynamically. 

We used ImageKit to host all the images for the API. Copied the image URL and added it to our database in Hasura Cloud. 

## Additional Features and Summary
These are some of the features we weren't able to implement before launching Rocketmeme. Though we are currently working on them so keep an eye out for the next release. 👀

- User Authentication
- Meme uploads by users.
- Users upvote and downvote memes.
- Meme categories page.

## Last Words
Thank you so much 🤩 **Hashnode** and **Hasura** for putting together this hackathon and to you reading this right now, I say a big thank you for taking out your time to go through this article. I genuinely appreciate it.

Rocketmeme is completely open-source so anyone willing to help collaborate in adding new features is most welcome to make a pull request, not just with code but any contribution that can make the project more suitable would be appreciated as well. And with that, I wrap up this article and hope to get your feedback for Rocketmeme in the comments below or the [feedback section](https://www.rocketmeme.com/contact) in rocketmeme.

## Links
- [Live Preview](https://rocketmeme.com)
- [GitHub Repository](https://github.com/Evavic44/rocketmeme)
- [API Endpoint](https://rocketmeme-user.hasura.app/v1/graphql)
- [API Documentation](https://github.com/Evavic44/rocketmemes-api)
- [Hasura Cloud](https://cloud.hasura.io/)