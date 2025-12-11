# Week 1: Plant Disease Classification - Getting Started 🌱

Hey everyone! 👋 

## Dataset

We'll be using the PlantVillage dataset for this project:
- **Link**: [PlantVillage Dataset on Kaggle](https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset/data)

### Setup Notes
- Download instructions are available on Kaggle's website
- For EDA, use available Kaggle notebooks instead of downloading the entire dataset locally
- We're assuming you can handle the basic setup (downloading dataset, environment configuration)

## Week 1 Requirements

### Must-Do Resources (Compulsory)

Complete all of these resources and implement the concepts:

1. **Neptune.ai EDA Guide** (Image datasets exploration)
   - Focus: Class imbalance, augmentations, small objects
   - Link: [Data Exploration for Image Segmentation and Object Detection](https://neptune.ai/blog/data-exploration-for-image-segmentation-and-object-detection)

2. **OpenCV Crash Course** (3 hours)
   - Focus: Image manipulation basics
   - Link: [OpenCV University Free Courses](https://opencv.org/university/free-courses/)

3. **Fast.ai Lesson 1** (90 minutes)
   - Focus: Build your first image classifier
   - Link: [Fast.ai Practical Deep Learning - Lesson 1](https://course.fast.ai/Lessons/lesson1.html)

4. **Plant Disease Tutorial** (45 minutes)
   - Focus: End-to-end CNN project with Docker
   - Link: [YouTube Tutorial](https://www.youtube.com/watch?v=L-Tqf1w5d0I)

5. **PlantVillage Dataset Exploration** (45 minutes)
   - Focus: Explore the dataset, perform basic EDA
   - Link: [Kaggle Dataset](https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset)

**What This Covers**: PyTorch basics, vision fundamentals, and EDA – everything you need before diving into federated learning with Flower, FastAPI, and deployment.

### Optional Resources (If You Finish Early)

Want more depth? Check these out:

- **Hugging Face Computer Vision Course**: [HF CV Course](https://huggingface.co/learn/computer-vision-course)
- **PyImageSearch Free Crash Course**: [OpenCV + Deep Learning Crash Course](https://pyimagesearch.com/free-opencv-computer-vision-deep-learning-crash-course/)

## Week 1 Best Practices 💡

### EDA Best Practices

**Document Your Findings**
- Keep a `learnings.md` file to note interesting observations and surprises
- Screenshot visualizations - you'll need them for presentations later
- Don't just count images - understand what makes this problem challenging

**Key Things to Analyze**
- Class distribution: Are some diseases underrepresented?
- Image quality: Check for blurry images, lighting variations, background differences
- Visual similarity: Which disease classes look similar to each other?
- Image properties: Resolution variations, aspect ratios, color distributions

**Go Beyond Basic Statistics**
- Create side-by-side visualizations (5-10 images per class)
- Test if YOU can distinguish between similar diseases visually
- Look for patterns: Do certain plants have more consistent image quality?

### OpenCV Learning Strategy

**Active Practice (Don't Just Watch)**
- After learning each concept, test it on 2-3 PlantVillage images immediately
- Create an `opencv_experiments.ipynb` for quick tests
- Try these mini-exercises:
  - Load, resize, and display images
  - Convert between color spaces (RGB, HSV) - see if diseases show up differently
  - Apply blur, edge detection - understand which operations preserve disease features

**Focus Areas for This Week**
- Image loading and basic operations (CRITICAL)
- Resizing and transformations (CRITICAL)
- Color space conversions
- Skip advanced topics for now - revisit when needed

### Fast.ai & PyTorch Fundamentals

**Code Along Actively**
- Pause every 10 minutes and implement what was shown
- Don't just watch - type the code yourself and experiment
- Try replacing their examples with PlantVillage data

**Master These PyTorch Basics**
- Tensor operations: reshaping, indexing, concatenation
- Understanding `DataLoader`: batch size, shuffle, num_workers
- Tensor shapes: Always print and verify `[batch, channels, height, width]`
- Moving tensors between CPU and GPU

**Common Mistakes to Avoid**
- Not checking tensor shapes at each step
- Forgetting image normalization (divide by 255)
- Mixing up dimension ordering

### Time Management Tips

**Strategic Resource Allocation**
- **OpenCV (3 hrs)**: Focus heavily on Hour 1-2 (basics & transformations), skim Hour 3
- **EDA**: Spend max 2 days - you can always revisit later
- **Neptune Guide**: Read actively with PlantVillage open in another tab
- If stuck >30 mins on something, ask in the group!

**Divide and Conquer** (for teams)
- Person A: Deep dive OpenCV, create cheat sheet
- Person B: Thorough EDA, document insights
- Person C: PyTorch fundamentals, share code snippets
- Everyone: Watch Plant Disease tutorial together, discuss afterward

### Code Quality from Day 1

**Organization**
- Use meaningful notebook/file names: `01_EDA.ipynb`, `02_opencv_experiments.ipynb`
- Add markdown cells explaining what each code section does
- Comment your code - your teammates (and future you) will thank you

**Version Control**
- Use Git properly: meaningful commit messages ("Add class distribution analysis" not "Update file")
- Commit frequently - don't wait until everything is perfect
- Each person work on separate notebooks to avoid merge conflicts

### Collaboration Tips

**Daily Check-ins (10 mins)**
- Share: "Today I learned X, struggled with Y, tomorrow I'll tackle Z"
- Post interesting code snippets or visualizations in the group
- Help debug together - explaining problems helps understanding

**Knowledge Sharing**
- Create shared Google Doc/Notion with key learnings and resources
- Screenshot important parts of tutorials for quick reference
- Build a team FAQ as questions come up

## Week 1 Goal & Deliverables

By the end of Week 1, you should have:

✅ **Complete EDA notebook** with:
- Class distribution visualization
- Sample image grid (multiple images per class)
- Image resolution/size analysis
- At least 2-3 meaningful insights about the dataset

✅ **Solid fundamentals**:
- Comfortable loading and manipulating images with OpenCV
- Understanding of basic PyTorch operations
- Familiarity with image preprocessing concepts

✅ **Documentation**:
- Clean, well-commented code
- Notes on interesting findings and questions for later
- Understanding of what makes this problem challenging

**Remember**: This week is about building strong foundations, not racing ahead. Focus on understanding concepts deeply rather than just completing checkboxes.

**Next Steps**: We'll use these foundations to scale to federated systems + production deployment 🚀

## Questions?

Drop them in the group! We're here to help.
