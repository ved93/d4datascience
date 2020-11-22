---
toc: true
hide: true
layout: post
description: Its very hard to keep up with new information and content in data science.
categories: [blogs, data science, ]
title: The Best Blogs and Newsletters in Data Science
---



For example, imagine we are to sample 5 lines randomly from a 6-line file. Call i the line number of the input, and N the size of sample desired. For the first 5 lines (where i < = N), our sample fills entirely. (For the non-Perl hackers: the current line number i is held by the variable $., just as the special variable $_ holds the current line value).

It's at successive lines of input that the probabilistic sampling starts: the 6th line has a 5/6th (N/i) chance of being sampled, and if chosen, it will replace one of the previously 5 chosen lines with a 1/5 chance: leaving them a (5/6 * 1/5) = 5/6 chance of being sampled. Thus all 6 lines have an equal chance of being sampled.

In general, as more lines are seen, the chance that any additional line is chosen for the sample falls; but the chance that any previously chosen line could be replaced grows. These two balance such that the probability for any given line of input to be sampled is identical.

A more sophisticated variation of this algorithm is one that can take into consideration a weighted sampling.





import sys
import random

if len(sys.argv) == 3:
    input = open(sys.argv[2],'r')
elif len(sys.argv) == 2:
    input = sys.stdin;
else:
    sys.exit("Usage:  python samplen.py <lines> <?file>")

N = int(sys.argv[1]);
sample = [];

for i,line in enumerate(input):
    if i < N:
        sample.append(line)
    elif i >= N and random.random() < N/float(i+1):
        replace = random.randint(0,len(sample)-1)
        sample[replace] = line

for line in sample:
    sys.stdout.write(line)