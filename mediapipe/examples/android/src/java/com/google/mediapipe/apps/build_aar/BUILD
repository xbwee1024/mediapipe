load("//mediapipe/java/com/google/mediapipe:mediapipe_aar.bzl", "mediapipe_aar")

# Note: execute the following command to take effect of build script changing
# `rm -rf bazel-bin/mediapipe/java/com/google/mediapipe/`
# 
# calculators should be built into libmediapipe_jni.so
mediapipe_aar(
    name = "mediapipe_framework",
    # srcs = ["//mediapipe/java/com/google/mediapipe/solutioncore:java_src"],   # uncomment this to build original solutions
    srcs = ["//mediapipe/java/com/google/mediapipe/framework/image:java_src"],  # uncomment this to build customized solutions
    calculators = [
        "//mediapipe/graphs/face_detection:mobile_calculators",
        "//mediapipe/graphs/face_mesh:mobile_calculators",
        "//mediapipe/graphs/hand_tracking:mobile_calculators",
        "//mediapipe/graphs/holistic_tracking:holistic_tracking_gpu_deps",
    ],
    assets = [
        "//mediapipe/graphs/holistic_tracking:holistic_tracking_gpu.binarypb",
        "//mediapipe/modules/face_detection:face_detection_short_range.tflite",
        "//mediapipe/modules/face_landmark:face_landmark.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_full.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_lite.tflite",
        "//mediapipe/modules/hand_landmark:handedness.txt",
        "//mediapipe/modules/holistic_landmark:hand_recrop.tflite",
        "//mediapipe/modules/pose_detection:pose_detection.tflite",
        "//mediapipe/modules/pose_landmark:pose_landmark_full.tflite",
    ],
    assets_dir = "",
)

# MUST ADD `.aar` suffix to generate AAR, or just `*.jar` generated
#
# build with bazel build -c opt --strip=ALWAYS --host_crosstool_top=@bazel_tools//tools/cpp:toolchain \
#   --fat_apk_cpu=arm64-v8a,armeabi-v7a --legacy_whole_archive=0 --features=-legacy_whole_archive \
#   --copt=-fvisibility=hidden --copt=-ffunction-sections --copt=-fdata-sections --copt=-fstack-protector \
#   --copt=-Oz --copt=-fomit-frame-pointer --copt=-DABSL_MIN_LOG_LEVEL=2 --linkopt=-Wl,--gc-sections,--strip-all \
#   //mediapipe/examples/android/src/java/com/google/mediapipe/apps/build_aar:mediapipe_xxx.aar
android_library(
    name = "mediapipe_holistic",
    srcs = [],
    assets = [
        "//mediapipe/graphs/holistic_tracking:holistic_tracking_gpu.binarypb",
        "//mediapipe/modules/face_detection:face_detection_short_range.tflite",
        "//mediapipe/modules/face_landmark:face_landmark.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_full.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_lite.tflite",
        "//mediapipe/modules/hand_landmark:handedness.txt",
        "//mediapipe/modules/holistic_landmark:hand_recrop.tflite",
        "//mediapipe/modules/pose_detection:pose_detection.tflite",
        "//mediapipe/modules/pose_landmark:pose_landmark_full.tflite",
    ],
    assets_dir = "",
    javacopts = ["-Acom.google.auto.value.AutoBuilderIsUnstable"],
    manifest = ":AndroidManifest.xml",
    visibility = ["//visibility:public"],
    deps = [
        "//mediapipe/framework/formats:classification_java_proto_lite",
        "//mediapipe/framework/formats:landmark_java_proto_lite",
        "//mediapipe/java/com/google/mediapipe/framework:android_framework",
        "//mediapipe/java/com/google/mediapipe/solutioncore:solution_base",
        "//third_party:autovalue",
        "@maven//:androidx_annotation_annotation",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
    ],
)

android_library(
    name = "mediapipe_hands",
    # srcs = ["//mediapipe/java/com/google/mediapipe/solutions/hands:java_src"],    # uncomment this to build original solutions
    srcs = [],                                                                      # uncomment this to build customized solutions, just asserts needed
    assets = [
        "//mediapipe/modules/hand_landmark:hand_landmark_full.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_lite.tflite",
        "//mediapipe/modules/hand_landmark:hand_landmark_tracking_cpu_image.binarypb",
        "//mediapipe/modules/hand_landmark:hand_landmark_tracking_gpu_image.binarypb",
        "//mediapipe/modules/hand_landmark:handedness.txt",
        "//mediapipe/modules/palm_detection:palm_detection_full.tflite",
        "//mediapipe/modules/palm_detection:palm_detection_lite.tflite",
    ],
    assets_dir = "",
    javacopts = ["-Acom.google.auto.value.AutoBuilderIsUnstable"],
    manifest = ":AndroidManifest.xml",
    visibility = ["//visibility:public"],
    deps = [
        "//mediapipe/framework/formats:classification_java_proto_lite",
        "//mediapipe/framework/formats:landmark_java_proto_lite",
        "//mediapipe/java/com/google/mediapipe/framework:android_framework",
        "//mediapipe/java/com/google/mediapipe/solutioncore:solution_base",
        "//third_party:autovalue",
        "@maven//:androidx_annotation_annotation",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
    ],
)

android_library(
    name = "mediapipe_facemesh",
    # srcs = ["//mediapipe/java/com/google/mediapipe/solutions/facemesh:java_src"],     # uncomment this to build original solutions
    srcs = [],                                                                          # uncomment this to build customized solutions, just asserts needed
    assets = [
        "//mediapipe/modules/face_detection:face_detection_short_range.tflite",
        "//mediapipe/modules/face_landmark:face_landmark.tflite",
        "//mediapipe/modules/face_landmark:face_landmark_with_attention.tflite",
        "//mediapipe/modules/face_landmark:face_landmark_front_cpu_image.binarypb",
        "//mediapipe/modules/face_landmark:face_landmark_front_gpu_image.binarypb",
    ],
    assets_dir = "",
    javacopts = ["-Acom.google.auto.value.AutoBuilderIsUnstable"],
    manifest = ":AndroidManifest.xml",
    visibility = ["//visibility:public"],
    deps = [
        "//mediapipe/framework/formats:landmark_java_proto_lite",
        "//mediapipe/java/com/google/mediapipe/framework:android_framework",
        "//mediapipe/java/com/google/mediapipe/solutioncore:solution_base",
        "//third_party:autovalue",
        "@maven//:androidx_annotation_annotation",
        "@maven//:com_google_code_findbugs_jsr305",
        "@maven//:com_google_guava_guava",
    ],
)
