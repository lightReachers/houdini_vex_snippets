# Welcome to Houdini Vex Snippets!

Hi, These are my personal vex snippets which I found handy for most of my Houdini workflow


## Get constant value for i attrib for "n" frames w.r.t Frames 

    int n = chi("number_frames");
    f@i = rint(@Frame/n)*n;
## Get step segments selection int attrib from noise 

    i@segment = int(floor(@noise*chi("steps")));    // @noise is a noise value, can use attrib noise sop or attrib vop for these 

## Get a chunked clustered mask (ramped )from cluster points on points

    int cluster_npt = nearpoint(1, @P);
    vector cluster_pos = point(1, "P", cluster_npt);
    vector posbox = relbbox(0, cluster_pos);
    float normalize_height = posbox.y;

    if (normalize_height > chf("SLider")) {
        @Cd = set(1, 0, 0);
        i@active = 1; 
    }
