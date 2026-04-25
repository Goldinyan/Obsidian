install translate aspell dict jq lynx 



#!/bin/bash

compact=false

# Argumente parsen
if [ "$1" = "-c" ] || [ "$1" = "--compact" ]; then
    compact=true
    word="$2"
else
    word="$1"
fi

if [ -z "$word" ]; then
    echo "Usage: $0 [-c|--compact] <word>"
    exit 1
fi

# Rechtschreibung prüfen
suggestions=$(echo "$word" | aspell -a | grep '^&')

if [ "$compact" = true ]; then
    echo "Suggestions:"
    if [ -n "$suggestions" ]; then
        echo "$suggestions"
    else
        echo "Spelling seems correct"
    fi

    echo
    echo "Definition (first line):"
    dict "$word" | head -n 5
    exit 0
fi

# Normalmodus
echo "Checking spelling..."
if [ -n "$suggestions" ]; then
    echo "Did you mean:"
    echo "$suggestions"
else
    echo "Spelling seems correct"
fi

echo
echo "Definition:"
dict "$word" | head -n 50

