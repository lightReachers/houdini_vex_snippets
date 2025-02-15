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
    
 ## Get n unique point groups from n values of a int attrubutes on points

    i@cluster_id = nearpoint(1, @P);    //  cluster_id attr on points
    setpointgroup(0, sprintf('cluster_%03i', i@cluster_id), @ptnum, 1); 

 ## Sop Volume vdb Fog with noises

    vector moiselmomoise(QP*0.2,5,0.1,1);
    @densitysanoise(QP*0.5+set(@Time*0,0,0)+noisel*@Time,5,0.5,1);
   
