# Welcome to Houdini Vex Snippet!

Hi, This is my personal vex snippet which I found handy for most of my Houdini workflow


## Get constant value for i attrib for "n" frames w.r.t Frames 

    int n = chi("number_frames");
    f@i = rint(@Frame/n)*n;
