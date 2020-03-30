#!/bin/bash


# Check given vars 

if [ ! -d "$1" ]
then
    read -p "Write input dir: " inputPath
else
    inputPath=$1
fi

if [ ! -d "$2" ]
then
    read -p "Write output dir: " outputPath
else
    outputPath=$2
fi

echo "The file will be copyed from $inputPath to $outputPath"


# If there isn't any output dirs, then creates them

if [ ! -d $outputPath/gif ]
then
    mkdir $outputPath/gif
fi

if [ ! -d $outputPath/video ]
then
    mkdir $outputPath/video
fi

if [ ! -d $outputPath/image ]
then
    mkdir $outputPath/image
fi

# File name
i=1


checker () {
    #Check for every file and dir in given dir
    for file in "$1"/*
    do
        # Get extension
        extension="${file##*.}"

        if [[ -d $file ]]
        then
            # If returns a dir, recall the function
            echo "DIR: $file"
            checker "$file"
        elif [[ -e $file ]]
        then
            # Analize extensions
            case "$extension" in
            "gif")
                #echo "GIF: $file"
                cp "$file" "$outputPath"/gif/$i.gif
                i=$((i+1))
                ;;
            "mp4")
                #echo "MP4: $file"
                cp "$file" "$outputPath"/video/$i.mp4
                i=$((i+1))
                ;;
            "jpg")
                #echo "JPG: $file"
                cp "$file" "$outputPath"/image/$i.jpg
                i=$((i+1))
                ;;
            "png")
                #echo "PNG: $file"
                cp "$file" "$outputPath"/image/$i.png
                i=$((i+1))
                ;;
            *)
                # Unknown file
                echo "OTH: $file $extension"
                ;;
            esac
        fi
    done
}


checker "$1"