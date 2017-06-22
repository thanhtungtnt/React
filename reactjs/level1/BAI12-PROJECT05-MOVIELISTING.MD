# PROJECT 05 - REACT ROUTER - MOVIE LISTING

## Nội dung:
* Tạo 1 SPA (Single Page Application)
* 1 trang có nhiều Router khác nhau

## Step by Step:

### 0. Cài package `create-react-app` để tạo project trong bài này.

```
npm install -g create-react-app
```

### 1. Chỉnh sửa code như sau và test chạy thử trước

* index.js
```
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';


ReactDOM.render(
  <App />,
  document.getElementById('app')
);
```

* App.js
```
import React, { Component } from 'react';
import logo from './svg/logo.svg';
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
        <div className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h2>Welcome to React</h2>
        </div>

        <p className="App-intro">
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
      </div>
    );
  }
}

export default App;
```

### 2. Thêm dữ liệu DEMO

* Tạo file movie.json, các Data item khác các bác tự thêm để demo nhé

```
[
    {
        "id": 1,
        "name": "The Hateful Eight",
        "director": "Quentin Tarantino",
        "released": "December 25, 2015",
        "image": "http://resizing.flixster.com/TnduRpSjWsBCj88PlUV5Q2dZX0I=/320x474/v1.bTsxMTI4NTM1NDtqOzE3MjE0OzIwNDg7ODEwMDsxMjAwMA",
        "description": "Set six or eight or twelve years after the Civil War, a stagecoach hurtles through the wintry Wyoming landscape. The passengers, bounty hunter John Ruth and his fugitive Daisy Domergue, race towards the town of Red Rock where Ruth, known in these parts as The Hangman, will bring Domergue to justice. Along the road, they encounter two strangers: Major Marquis Warren, a black former union soldier turned infamous bounty hunter, and Chris Mannix, a southern renegade who claims to be the town's new Sheriff. Losing their lead on the blizzard, Ruth, Domergue, Warren and Mannix seek refuge at Minnie's Haberdashery, a stagecoach stopover on a mountain pass. When they arrive at Minnie's, they are greeted not by the proprietor but by four unfamiliar faces. Bob, who's taking care of Minnie's while she's visiting her mother, is holed up with Oswaldo Mobray, the hangman of Red Rock, cow-puncher Joe Gage (Madsen), and Confederate General Sanford Smithers. As the storm overtakes the mountainside stopover, our eight travelers come to learn they may not make it to Red Rock after all...",
        "reviews": [
            {
                "title": "Hated it",
                "body": "This movie is dumb!",
                "author": "John Pete"
            }
        ]
    },
    {
        "id": 2,
        "name": "Reservoir Dogs",
        "director": "Quentin Tarantino",
        "released": "October 23, 1992",
        "image": "http://resizing.flixster.com/kQvsg7IIyBcfWZ9cXOKIiDTIteY=/320x480/v1.bTsxMTE3NzYzMjtqOzE3MjIxOzIwNDg7ODAwOzEyMDA",
        "description": "In 1992, Reservoir Dogs transformed Quentin Tarantino practically overnight from an obscure, unproduced screenwriter and part-time actor to the most influential new filmmaker of the 1990s. The story looks at what happens before and after (but not during) a botched jewelry store robbery organized by Joe Cabot (Lawrence Tierney). Mr. White (Harvey Keitel) is a career criminal who takes a liking to newcomer Mr. Orange (Tim Roth) and enjoys showing him the ropes. Mr. Pink (Steve Buscemi) is a weaselly loner obsessed with professionalism. Mr. Blonde (Michael Madsen) has just gotten out of jail after taking the rap on a job for Cabot; he's grateful for the work but isn't the same person he used to be. While Mr. Blonde goes nuts during the heist, the thieves are surprised by the sudden arrival of the police, and Mr. Pink is convinced one of their team is a cop. So who's the rat? What do they do about Mr. Blonde? And what do they do with Mr. Orange, who took a bullet in the gut and is slowly bleeding to death? Reservoir Dogs jumps back and forth between pre- and post-robbery events, occasionally putting the narrative on pause to let the characters discuss such topics as the relative importance of tipping, who starred in Get Christie Love!, and what to do when you enter a men's room full of cops carrying a briefcase full of marijuana. ~ Mark Deming, Rovi",
        "reviews": [
            {
                "title": "Tarantino does it again!",
                "body": "If this movie got stuck in our laserdisk player, I wouldn't mind!",
                "author": "Rex Guy"
            }
        ]
    }
]
```

* Import vào file `App.js` của chúng ta.

```
import React from 'react';
import movies from '../movies.json';
```

### 3. Tùy chỉnh giao diện trang HOME

#### Yêu cầu:

* Trang chủ show 4 phim (TOP 4 phim)
* Mỗi một phim ta đặt tên là: FeaturedMovie => cần tạo Component `FeaturedMovie`

### App.js

```
import React from 'react';
import movies from '../movies.json';
import FeaturedMovie from './FeaturedMovie';

const Home = () => {
  const topFour = movies.slice(0, 4);

  return (
    <div>
      <h2 className="featured-movies__header">
        Featured Movies
      </h2>

      <hr />

      <div className="featured-movies">
        {topFour.map((movie, i) => (
          <FeaturedMovie
            movie={movie}
            key={i}
          />
        ))}
      </div>
    </div>
  );
};

export default Home;
```

## Source code 
* [Link source code hoàn thiện](https://github.com/nvminhtu/React/tree/master/reactjs/project05-movie-listing)