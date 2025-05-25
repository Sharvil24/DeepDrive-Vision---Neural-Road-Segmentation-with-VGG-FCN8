<h1 align="center">🚗 DeepDrive-Vision - Neural Road Segmentation with VGG-FCN8</h1>

<h2>📋 Overview</h2>
<p>This project implements a deep learning-based road segmentation system that accurately identifies and segments road areas from street-view images. The model uses semantic segmentation techniques to distinguish road surfaces from other elements in urban environments.</p>

<h3>Key Features:</h3>
<ul>
    <li>Accurate road surface detection in various lighting conditions</li>
    <li>Robust segmentation for urban and suburban scenes</li>
    <li>Clear visualization with color-coded segmentation masks</li>
    <li>Efficient inference on test images</li>
</ul>

<h2>🎯 What is Road Segmentation?</h2>
<p>Road segmentation is a computer vision task that involves identifying and delineating road areas in images. This technology is crucial for:</p>
<ul>
    <li><strong>Autonomous Vehicles:</strong> Understanding drivable areas for navigation</li>
    <li><strong>Traffic Management:</strong> Analyzing road usage and conditions</li>
    <li><strong>Urban Planning:</strong> Mapping and monitoring road infrastructure</li>
    <li><strong>Safety Applications:</strong> Detecting road boundaries and hazards</li>
</ul>

<h2>📸 Sample Data</h2>
<p>Below is an example of our training data, showing an input image alongside its corresponding ground truth mask:</p>

<table>
    <tr>
        <td align="center">
            <img src="img1_input.jpg" alt="Sample Input Image" width="400">
            <br>
            <em>Input Image</em>
        </td>
        <td align="center">
            <img src="img1_mask.jpg" alt="Sample Ground Truth Mask" width="400">
            <br>
            <em>Ground Truth Mask</em>
        </td>
    </tr>
</table>

<p>The yellow regions in the mask represent road areas, while purple regions indicate non-road areas.</p>

<h2>🔄 Model Performance</h2>
<p>Here we demonstrate the model's segmentation capabilities on test images:</p>

<h3>Before and After Prediction</h3>
<table>
    <tr>
        <td align="center">
            <img src="img2_input.jpg" alt="Test Image" width="300">
            <br>
            <em>Original Image</em>
        </td>
        <td align="center">
            <img src="img2_truth.jpg" alt="Ground Truth" width="300">
            <br>
            <em>Ground Truth</em>
        </td>
        <td align="center">
            <img src="img2_predicted.jpg" alt="Predicted Mask" width="300">
            <br>
            <em>Predicted Mask (Heatmap)</em>
        </td>
    </tr>
</table>

<h3>Refined Prediction</h3>
<table>
    <tr>
        <td align="center">
            <img src="img3_input.jpg" alt="Test Image" width="300">
            <br>
            <em>Original Image</em>
        </td>
        <td align="center">
            <img src="img3_truth.jpg" alt="Ground Truth" width="300">
            <br>
            <em>Ground Truth</em>
        </td>
        <td align="center">
            <img src="img3_predicted.jpg" alt="Refined Prediction" width="300">
            <br>
            <em>Refined Prediction</em>
        </td>
    </tr>
</table>

<h2>🚀 Real-World Applications</h2>
<p>Our road segmentation model has been tested on various real-world scenarios. Below are examples showcasing the model's performance in different conditions:</p>

<h3>Urban Street Scenes</h3>
<table>
    <tr>
        <td align="center">
            <img src="img4_input.jpg" alt="Urban Scene 1" width="400">
            <br>
            <em>Original Street View</em>
        </td>
        <td align="center">
            <img src="img4_predicted.jpg" alt="Segmented Road 1" width="400">
            <br>
            <em>Segmented Road (Highlighted in Red)</em>
        </td>
    </tr>
</table>

<h3>Highway Conditions</h3>
<table>
    <tr>
        <td align="center">
            <img src="img5_input.jpg" alt="Highway Scene" width="400">
            <br>
            <em>Highway Input</em>
        </td>
        <td align="center">
            <img src="img5_predicted.jpg" alt="Highway Segmentation" width="400">
            <br>
            <em>Highway Road Segmentation</em>
        </td>
    </tr>
</table>

<h3>Suburban Roads</h3>
<table>
    <tr>
        <td align="center">
            <img src="img6_input.jpg" alt="Suburban Scene" width="400">
            <br>
            <em>Suburban Street</em>
        </td>
        <td align="center">
            <img src="img6_predicted.jpg" alt="Suburban Segmentation" width="400">
            <br>
            <em>Road Area Detection</em>
        </td>
    </tr>
</table>

<h3>Challenging Lighting Conditions</h3>
<table>
    <tr>
        <td align="center">
            <img src="img7_input.jpg" alt="Low Light Scene" width="400">
            <br>
            <em>Low Light/Shadow Conditions</em>
        </td>
        <td align="center">
            <img src="img7_predicted.jpg" alt="Low Light Segmentation" width="400">
            <br>
            <em>Robust Segmentation Result</em>
        </td>
    </tr>
</table>

<h2>📊 Technical Implementation</h2>

<h3>🔧 Technologies Used</h3>
<ul>
    <li><strong>TensorFlow/Keras</strong> - Deep learning framework</li>
    <li><strong>OpenCV</strong> - Image processing and video handling</li>
    <li><strong>NumPy & Pandas</strong> - Data manipulation</li>
    <li><strong>Matplotlib</strong> - Visualization</li>
    <li><strong>VGG16</strong> - Pre-trained backbone network</li>
</ul>

<h3>📁 Dataset Structure</h3>
<p>The project uses the KITTI road segmentation dataset with the following structure:</p>
<ul>
    <li><strong>Training Images:</strong> Located in <code>/training/image_2/</code></li>
    <li><strong>Ground Truth Masks:</strong> Located in <code>/training/gt_image_2/</code></li>
    <li><strong>Data Split:</strong>
        <ul>
            <li>80% Training</li>
            <li>10% Validation</li>
            <li>10% Testing</li>
        </ul>
    </li>
    <li><strong>Image Categories:</strong> um, umm, and uu (different road scenarios)</li>
</ul>

<h3>🏗️ Model Architecture: VGG-FCN8</h3>
<p>The implementation uses a <strong>Fully Convolutional Network (FCN-8)</strong> architecture with VGG16 as the backbone:</p>
<ul>
    <li><strong>Encoder:</strong> Pre-trained VGG16 layers (frozen weights from ImageNet)</li>
    <li><strong>Skip Connections:</strong> From pool3, pool4, and pool5 layers</li>
    <li><strong>Decoder:</strong> Upsampling layers with bilinear interpolation</li>
    <li><strong>Output:</strong> Single channel binary mask with sigmoid activation</li>
</ul>

<h3>📝 Implementation Workflow</h3>

<h4>1. Data Preprocessing</h4>
<ul>
    <li>Images resized to 128×128 pixels</li>
    <li>Normalization to [0, 1] range</li>
    <li>Binary mask generation from color-coded ground truth:
        <ul>
            <li>Road pixels: [255, 0, 255] → 1</li>
            <li>Non-road pixels: [255, 0, 0] → 0</li>
        </ul>
    </li>
    <li>Data augmentation: Random horizontal flipping</li>
</ul>

<h4>2. Training Configuration</h4>
<ul>
    <li><strong>Optimizer:</strong> Adam</li>
    <li><strong>Loss Function:</strong> Binary Cross-Entropy</li>
    <li><strong>Metrics:</strong> Mean IoU (Intersection over Union)</li>
    <li><strong>Batch Size:</strong> 32</li>
    <li><strong>Epochs:</strong> 200 (with early stopping)</li>
    <li><strong>Callbacks:</strong>
        <ul>
            <li>TensorBoard logging</li>
            <li>Early stopping (patience=10)</li>
            <li>Model checkpointing (saves best model)</li>
            <li>Custom display callback for visualization</li>
        </ul>
    </li>
</ul>

<h4>3. Post-Processing</h4>
<ul>
    <li>Threshold prediction at 0.5 for binary mask</li>
    <li>Red overlay visualization using OpenCV's <code>cv2.addWeighted()</code></li>
    <li>Resize output to original dimensions</li>
</ul>

<h3>📈 Key Features Implemented</h3>
<ul>
    <li><strong>Efficient Data Pipeline:</strong> TensorFlow data API with prefetching and parallel processing</li>
    <li><strong>Transfer Learning:</strong> Leverages pre-trained VGG16 features</li>
    <li><strong>Real-time Visualization:</strong> Live prediction display during training</li>
    <li><strong>Modular Design:</strong> Separate functions for preprocessing, training, and inference</li>
</ul>

<h3>💡 Key Technical Features</h3>
<ul>
    <li>Efficient TensorFlow data pipeline with prefetching</li>
    <li>Transfer learning from VGG16</li>
    <li>Real-time prediction visualization</li>
    <li>Complete end-to-end image segmentation pipeline</li>
</ul>

<p>The implementation demonstrates a production-ready road segmentation system that can handle static images, making it suitable for applications like autonomous driving systems, urban planning, and road infrastructure analysis.</p>

<h2>🎯 Future Improvements</h2>
<ul>
    <li>Multi-class segmentation (lanes, sidewalks, crossings)</li>
    <li>Integration with 3D scene understanding</li>
    <li>Enhanced performance in adverse weather conditions</li>
    <li>Real-time optimization for embedded systems</li>
</ul>

<h2>📝 Conclusion</h2>
<p>This road segmentation system demonstrates robust performance across various road conditions and environments. The visual results show accurate delineation of road surfaces, which is essential for autonomous navigation and urban planning applications.</p>

<p><strong>Note:</strong> The red overlay in the predicted images represents the detected road area, providing clear visualization of the segmentation results.</p>
