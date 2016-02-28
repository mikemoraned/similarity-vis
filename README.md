Motivation

  Playing with extracting knowledge from slack metadata. For example, try to find something out about channels
  or people by looking at how they are related on slack.

Prerequisites

  python, virtualenv, pip
  # on mac you also need brew
  a slack api token (your-api-token below)

Install

  virtualenv venv
  source ./venv/bin/activate

  # on mac, you also need:
  brew install libffi

  pip install -r requirements.txt

Usage

  python --token your-api-token --size 3 --out summary.json
  python -m SimpleHTTPServer 8000
  # open http://localhost:8000