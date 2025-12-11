# Week 1: Plant Disease Classification - Getting Started 🌱

Hey everyone! 👋 

## Week 1 RoadMap
1. Create a Kaggle Account if you have none, link it with GitHub. 
2. Create a GitHub repository for WiDS 5.0 and add the notebook into that GitHub repo. 
3. Create the Kaggle notebook and using the add input button, add the dataset that we have given (directly pasting the link in the search bar that opens, leads to that dataset)
4. Read from neptune.ai and other sources if you want to, and come up with some more insights. 

## Dataset

We'll be using the PlantVillage dataset for this project:
- **Link**: [PlantVillage Dataset on Kaggle](https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset/data)

### Setup Notes
- Download instructions are available on Kaggle's website
- For EDA, use available Kaggle notebooks instead of downloading the entire dataset locally
- We're assuming you can handle the basic setup (downloading dataset, environment configuration)

## Week 1 Requirements

### Must-Do (Compulsory)

#### Coding Resources
These are notebooks that have used EDA techniques on different datasets. You are expected to read and replicate these for our dataset.

1.  Basic [Exploratory Data Analysis (EDA) for Image Datasets](https://www.kaggle.com/code/faldoae/exploratory-data-analysis-eda-for-image-datasets)

#### Reading Resources

Read these resources, and prepare content for the 2 minute presentations that we are going to have. 

1. **Neptune.ai EDA Guide** (Image datasets exploration)
   - Focus on Class imbalance, augmentations, small objects
   - Link: [Data Exploration for Image Segmentation and Object Detection](https://neptune.ai/blog/data-exploration-for-image-segmentation-and-object-detection)

2. **[MLDemystified](https://mldemystified.com/)**
	- Read the articles, they are very well explained, we will be trying to implement some 

### Optional 
Try and find some other methods, and 

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

### Code Quality from Day 1

**Organization**
- Use meaningful notebook/file names: `01_EDA.ipynb`, `02_opencv_experiments.ipynb`
- Add markdown cells explaining what each code section does

**Version Control**
- Use Github properly: meaningful commit messages ("Add class distribution analysis" not "Update file")
- Commit frequently - don't wait until everything is perfect
- Each person work on separate notebooks to avoid merge conflicts




## Week 1 Goal & Deliverables

By the end of Week 1, you should have:

✅ **Complete EDA notebook** with:
- Class distribution visualization
- Sample image grid (multiple images per class)
- Image resolution/size analysis
- At least 2-3 meaningful insights about the dataset

✅ **A Github repository, with appropriate name**
- After finishing with EDA, push that to github, this is done via kaggle itself. 

**Remember**: This week is about building strong foundations, not racing ahead. Focus on understanding concepts deeply rather than just completing checkboxes.

**Next Steps**: We'll use these foundations to scale to federated systems + production deployment 🚀

## Questions?

Drop them in the group! We're here to help.
