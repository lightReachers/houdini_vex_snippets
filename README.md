# Welcome to Houdini Vex Snippet!

Hi, This is my personal vex snippet which I found handy for most of my Houdini workflow


## Get constant value for i attrib for "n" frames w.r.t Frames 

    int n = chi("number_frames");
    f@i = rint(@Frame/n)*n;
## Get step segments selection int attrib from noise 

    i@segment = int(floor(@noise*chi("steps")));    // @noise is a noise value, can use attrib noise sop or attrib vop for these 
