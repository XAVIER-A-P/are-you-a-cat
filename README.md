

#  Are You A Cat ?

![Alt text]("C:\Users\HP\Downloads\cat.jpg")

###  Objective
This project explores MLOps and deep learning practices by building an end-to-end image classification pipeline that determines whether an uploaded selfie is of a cat. While the premise is playful, the real goal is to experiment with model training, deployment, and pipeline orchestration using modern tools like ZenML, MLflow, and Streamlit.



###  Solution Overview

- **Frameworks Used**: ZenML, TensorFlow Keras, MLflow, Streamlit, Deepchecks
- **Core Functionality**: Classify uploaded images as "cat" or "not cat" via a CNN model served through a Streamlit app



###  Pipeline Architecture

#### 1. Training Pipeline
- **Steps**: Data cleaning → Model training → Evaluation
- **Model**: 2D CNN built with TensorFlow Keras
- **Tracking**: MLflow autologging for metrics and hyperparameters
- **Tuning**: Manual tuning via `keras_tuner`
- **Performance**: Achieved recall of 0.8 and precision of 0.53 on hold-out test set

#### 2. Deployment Pipeline
- **Workflow**: Continuous deployment based on evaluation thresholds
- **Trigger**: Deploys model if it meets minimum recall and precision
- **Serving**: MLflow model server runs locally and updates automatically

#### 3. Inference Pipeline
- **Interface**: Streamlit app for user interaction
- **Functionality**: Accepts selfies, returns cat probability, stores feedback and images to S3
- **Future Plans**: Add SHAP explanations for interpretability



###  Data Details

- **Sources**: Cats & dogs dataset, selfies, random images
- **Composition**: 25% each of cats, dogs, selfies, and miscellaneous
- **Preprocessing**: Reshaping and normalization
- **Validation**: Deepchecks used ad-hoc for non-tabular data



###  Current Limitations & Future Enhancements

#### Data
- Label accuracy and duplication checks are pending
- Data validation not yet integrated into pipelines

#### Model & Training
- Local training on small datasets; cloud migration planned (e.g., SageMaker)
- Manual hyperparameter tuning; awaiting ZenML support
- No error analysis or classification threshold tuning
- No formal model validation step

#### Deployment
- Currently local via MLflow; future migration to Seldon/KServe

#### Monitoring
- Basic logging only; feedback stored but not yet analyzed
- No input validation, UI testing, or privacy safeguards

#### Orchestration
- Manual pipeline execution; plans to automate with Airflow
- Aspirations for continual learning without storing raw images

#### Miscellaneous
- Minimal testing coverage
- Dockerization under consideration



###  Next Steps
- Integrate SHAP for model interpretability
- Migrate training and deployment to cloud infrastructure
- Automate pipeline execution and monitoring
- Enhance data validation, model evaluation, and UI robustness





