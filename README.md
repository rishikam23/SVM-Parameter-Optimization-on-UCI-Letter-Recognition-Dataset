# SVM Parameter Optimization on UCI Letter Recognition Dataset
This project focuses on optimizing SVM parameters for a multi-class classification problem using the Letter Recognition dataset from the UCI repository.

---

## Objective
- Choose a multi-class dataset (5k–30k samples)
- Divide into 10 different 70:30 train-test splits
- Optimize SVM using 100 iterations (via Optuna)
- Log best accuracy and parameters per sample
- Plot convergence for the best-performing sample
---

## Dataset Info
- **Source**: [UCI Letter Recognition Dataset](https://archive.ics.uci.edu/ml/datasets/letter+recognition)
- **Samples**: 20,000
- **Classes**: 26 (A–Z)
- **Features**: 16 numerical features
---

## Exploratory Data Analysis (EDA)
- Class distribution (balanced)
  ![image](https://github.com/user-attachments/assets/f3b2112f-069a-4984-bdf2-050b395d4503)
- Feature correlations
  ![image](https://github.com/user-attachments/assets/e2ad991a-d960-4c5c-880f-7e1bd350469c)
- Boxplots for detecting spread & outliers
  ![image](https://github.com/user-attachments/assets/c3d74225-515b-4abb-a5ad-3c070488a3b8)
---

## Methodology
1. **Data Splitting**: The dataset is randomly split into 10 different training (70%) and testing (30%) sets to ensure robust evaluation.

2. **Model Selection**: We use `NuSVC` (a variant of SVM) suitable for multi-class classification.

3. **Parameter Tuning**: For each split, Optuna performs 100 iterations of hyperparameter tuning:
   - `kernel`: ['linear', 'rbf', 'poly', 'sigmoid']
   - `nu`: Continuous range from 0.01 to 1.0

4. **Evaluation**: For each train-test split, the model is trained on the training set and evaluated on the test set. Accuracy is recorded.

5. **Best Sample Analysis**: The split with the highest accuracy is identified, and its Optuna convergence graph is saved to visualize tuning progress.
---

## Model Used
- **Algorithm**: Nu-Support Vector Classification (`NuSVC`)
- **Tuning Technique**: `Optuna` (100 iterations)
- **Parameters Optimized**:
  - `kernel`: linear, rbf, poly, sigmoid
  - `nu`: [0.01, 1.0]
---

## Results Summary
### Results Table
| Sample | Best Accuracy | Best Parameters                |
|--------|----------------|-------------------------------|
| S1     | 0.86           | {'kernel': 'rbf', 'nu': 0.23} |
| S2     | ...            | ...                           |
| ...    | ...            | ...                           |

- Best performing sample: **S3**  
- Each row corresponds to a different train-test split.
- `Best Accuracy` indicates the highest test accuracy achieved during optimization.
- `Best Parameters` shows the kernel type and nu value selected by Optuna for that split.
  
- Convergence graph saved as `convergence_graph.png`
- `convergence_graph.png` displays the optimization history for the best-performing sample (S3).
- The Y-axis shows the objective value (accuracy), and the X-axis shows the number of trials.
- The plot helps visualize how quickly Optuna converged to the best solution.

---

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/rishikam23/SVM-Parameter-Optimization-on-UCI-Letter-Recognition-Dataset.git
   cd letter-recognition-svm-optimization
   ```
2. Install the required dependencies:
  ```bash
  pip install pandas numpy matplotlib seaborn scikit-learn optuna
  ```
3. Run the script for parameter optimization.
4. Check the results and convergence graph.
---

## License
This project is licensed under the MIT License - see the LICENSE file for details.

---

## Contributions
Community contributions are welcome — feel free to open an issue or submit a pull request to improve the project!

---
