---
author: fritzvd
draft: true
tags:
  - chess
date: 2025-12-17T06:49:23Z
title: Learning Chess (again) - Sicilian Defense
---

<link rel="stylesheet" href="/blog/chessboard.css">
<script src="https://code.jquery.com/jquery-3.5.1.min.js"
        integrity="sha384-ZvpUoO/+PpLXR1lu4jmpXWu80pZlYUAfxl5NsBMWOEPSjUn/6Z/hRTt8+pR6L4N2"
        crossorigin="anonymous"></script>

<script src="/blog/chessboard.js"></script>

As long as I can remember I have been trying to learn to play chess well. When I was six I learned to use the pieces and lost many a game since.

I'm not good at it at all. I still lose most of my games. But I still enjoy it, the puzzles, playing the game.

Over the last few weeks I've been getting back into it and trying out some openings.

At the moment I've been trying to play Sicilian Defence with black.

That would be opening with the c-pawn in response to the king's Pawn instead of the e or d-pawn, in order to get control of _the centre_:

1. e4 - c6

<div id="board-1" style="width: 400px"></div>

<script>
const sic = 'rnbqkbnr/pp1ppppp/8/2p5/4P3/8/PPPP1PPP/RNBQKBNR w KQkq - 0 1'
const board = Chessboard('board-1', sic)

setTimeout(function () {

  Array.from(document.querySelectorAll('img')).forEach(i =>{
    i.style['margin-top']='unset';
  })

},
200)
</script>
