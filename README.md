# Motivation

Playing with extracting knowledge from slack data or metadata. For example, try to find similar channels,
based on content.

# Prerequisites

* python3, virtualenv, pip
* a slack api token (API_TOKEN below)
    * see https://api.slack.com/bot-users, specifically https://my.slack.com/services/new/bot

# Install

    virtualenv venv
    source ./venv/bin/activate

    pip3 install -r requirements.txt

# Usage

## Setup defaults

    export API_TOKEN="your-api-token"

## Get base information

Find all messages, for any channels that have between 10 and 1000
recent messages

    python3 crawl.py --token $API_TOKEN

Analyse these messages, extracting what we need for building anything
with them

    python3 analyse.py

## Find similar channels

For a single channel, find top 10 similar channels

    python3 similarity.py --channel some-channel-name --topn 10

## Bulk Convert to channel similarities

Use analysed message content to find similarities between channels, and
convert this similarity to a distance measure, only allowing channels closer
than 0.8.

    python3 similarities.py --distance 0.8 --out content.sims.json

## Visualise channel similarity

    python3 visualise.py --in content.sims.json --out vis.json
    python3 -m http.server 8000 &
    open http://localhost:8000
