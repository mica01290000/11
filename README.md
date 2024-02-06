<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web AR Example</title>
    <script src="https://aframe.io/releases/1.2.0/aframe.min.js"></script>
    <script src="https://raw.githack.com/jeromeetienne/ar.js/master/aframe/build/aframe-ar.js"></script>
    <script src="https://threejs.org/build/three.js"></script>
</head>
<body>
    <a-scene embedded arjs="sourceType: webcam; debugUIEnabled: false;">
        <a-marker preset="hiro">
            <!-- 3D 模型將在此處顯示 -->
            <a-entity id="3dModel" position="0 0 0" scale="0.5 0.5 0.5" rotation="0 0 0" gltf-model="url(path/to/your/3d/model.glb)"></a-entity>
        </a-marker>

        <!-- 放置在標記外的場景 -->
        <a-entity camera></a-entity>
    </a-scene>

    <script>
        // 在此處換成你的其他 3D 模型的 URL
        const alternativeModels = [
            "path/to/your/alternative_model_1.glb",
            "path/to/your/alternative_model_2.glb",
            // 添加更多模型的 URL
        ];

        let currentModelIndex = 0;
        const modelEntity = document.getElementById("3dModel");

        // 在點擊畫面時更換 3D 模型
        document.body.addEventListener("click", () => {
            currentModelIndex = (currentModelIndex + 1) % alternativeModels.length;
            const newModelURL = alternativeModels[currentModelIndex];
            modelEntity.setAttribute("gltf-model", `url(${newModelURL})`);
        });
    </script>
</body>
</html>
