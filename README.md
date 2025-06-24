# Player-ReID

CROSS-CAMERA PLAYER MAPPING
--------------------------------------------------------------------------------------------------------------------
Step1: Use already existing yolo v11 type model to detect objects in the videos and giving each object an ID

Step2: Cut these detections out from both the videos and create embeddings for each detection using OSNet (Omni-Scale Feature Learning for Person Re-Identification)*

Step3: For each detected/tracked player in Video A:
-Extract feature embedding.
  1) Compare against all player embeddings in Video B using cosine similarity or Euclidean distance.
  2) Pick the match with the highest similarity.
-To improve matching:
  1) Temporal information — check if the players are doing similar actions at the same time in both videos.
  2) Geometric constraints — approximate field mapping (homography) between camera views to constrain possible matching locations.



Future Enhancements
Pose Matching: Incorporate pose estimation (e.g., OpenPose or MMPose) to improve matching based on player actions.
Temporal Features: Use video-based Re-ID models or RNNs over embeddings to capture sequence patterns.
Scene Geometry: Use camera calibration to map one camera view to another.



*These embeddings should be:
Robust to viewpoint change
Consistent across different camera angles



DEPENDENCIES/TOOLS
----------------------------------------------------------------------------------------------------------------------
pip install cv2, torch, numpy, ultralytics, torchreid, torchvision, scipy
