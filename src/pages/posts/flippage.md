---
title: 'Flippage'
description: "Flippage Introduction"
pubDate: '2023-06-25'
hero: '/images/110.jpg'
tags: ['astro']
layout: '../../layouts/BlogPostLayout.astro'

import BaseHead from '../components/Head/BaseHead.astro';
import Nav from '../components/Nav.astro';
import HomeHeader from '../components/HomeHeader.astro';
import Footer from '../components/Footer/Footer.astro'
import SearchInput from '../components/SearchInput.astro'

import type { HTMLAttributes } from 'astro/types';


let pageTitle = 'Flip page';
let pageDescription = 'This is Contact page';
let seoTitle = 'Search | Creek';
let seoDescription = '';

interface MarkdownFrontmatter {
  date: number;
  pubDate: string; // Add the pubDate property of type string
}

const title = 'Nomad AI 智能游牧时代';
const description = 'Nomad AI - Before die, do';


const allPosts = await Astro.glob<MarkdownFrontmatter>('./posts/*.md');
const sortedPosts = allPosts.sort((a, b) => new Date(b.frontmatter.pubDate).valueOf() - new Date(a.frontmatter.pubDate).valueOf());
---

<astro>
  // Define a function to toggle the "flipped" class on the flip container
  export function flipPage(event) {
    event.currentTarget.classList.toggle('flipped');
  }
</astro>

<div class="flip-container" on:click={flipPage}>
  <div class="flip-page">
    <div class="front-page">
      <!-- Content of the front page -->
    </div>
    <div class="back-page">
      <!-- Content of the back page -->
    </div>
  </div>
</div>

<style>
  .flip-container {
    perspective: 1000px;
    width: 200px;
    height: 200px;
  }

  .flip-page {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.6s;
  }

  .front-page,
  .back-page {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    backface-visibility: hidden;
  }
</style>
