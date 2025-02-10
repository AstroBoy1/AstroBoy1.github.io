---
layout: post
title:  "Kaggle FIDE Efficient Chess Engine Competition"
date:   2024-11-26 15:34:41 -0800
categories: jekyll update
---

This was my first time looking at chess engine code: [github link][code-link].
The goal of the competition was to keep the memory under 5Mib and the total file size under 64Kib.
I ended up trying out a variety of open source chess engines, and documenting
the memory usage, elo, and file size of each. Stockfish stood out as the strongest and cfish
was a more memory efficient version written in C.

To get the file size down, I took out the openings book, the endgame book, print statements,
960 support, and used 7z. One trick was that the platform didn't accept 7z, so I used 7z to compress the engine, then used gz to compress that because gz was an allowed format.

I made sure to track each change with either a new branch or commit, and ran a chess match of 20 rounds between
each new iteration to see that I hadn't broken anything. All of this went into a spreadsheet to make it easier to track.

The memory part was more difficult. It came down to seeing what parts of the program used the most memory.
I found that the transposition table used a sizeable portion, reducing this helped a lot.
The second component was the key size used for pawn caching.

It was interesting to note the deflation of Kaggle ratings over time as people's engines kept improving, but
started at the lowest rating. This made it a bit harder to judge the elo of chess engines because only
the two most recent active submissions were paired with other engines. Thus local testing was helpful; however,
not totally representative of the rating that would be obtained by Kaggle, since it's also not possible to know what other engines other people are using.

Near the end of the competition, I joined teams and got to make new friends across the world.
We learned how to collaborate as a team in different timezones, which
was a bit hard, but overall, a great learning experience.

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[code-link]: https://github.com/AstroBoy1/Cfish-light
