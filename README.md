# GstreamerExample

### Pipeline

#### 1
autovideosrc->videoconvert->capsfilter->tee->queue->autovideosink

#### 2
autovideosrc->videoconvert->capsfilter->tee->queue->vp8enc->rtpvp8enc->capsfilter->webrtcbin

#### 3

                                            queue->vp8enc->rtpvp8enc->capsfilter->webrtcbin
                                           /
                                           
autovideosrc->videoconvert->capsfilter->tee

                                           \
                                            queue->videoconvert->autovideosink
                                            
### How to work

Firstly, go to https://webrtc.nirbheek.in/ in Firefox. Note your id. Id changes every time the page reload. Run the application. Give id as input to application. Press "1" and allow media from Firefox. Pipeline is 2 that above and webrtc runs. Your view should be displayed in Firefox. If press "2", pipeline shold be like 3 then if press "3", pipeline should be like 2. if you press "2" second time, pipeline freezes.
