# Freight Rate Prediction Challenge

See `Freight_Rate_ML_Assessment.pdf` for the assessment instructions.

## What to do

1. Train and validate your model using `data/train_test.csv`.
2. Predict every load in `data/validation.csv`. Each load has a unique `load_id`.
3. Fill the matching `predicted_rate` values in `data/validation_predictions_template.csv` and save it as `validation_predictions.csv`.
4. Predict every row in `data/december_chart_inputs.csv` by filling its `predicted_rate` column.
5. Install the scorer requirements and run:

```bash
python -m pip install -r requirements.txt
python score.py --predictions validation_predictions.csv --december-predictions data/december_chart_inputs.csv
```

The scorer validates both files and creates `scorer_results/candidate_december.png`.

## Submit

- GitHub repository containing your code, dependencies, and run instructions
- `validation_predictions.csv`
- PDF or DOCX report containing your validation, data split approach and `candidate_december.png`
- 2-3 minute Loom link

## My code run instructions
```bash
python -m pip install -r requirements.txt

# to get all cleaned and validated data to use in training
python -m src.pipelines.data_pipeline

# use the cleaned data from data pipeline to train the models and get the final best model
python -m src.pipelines.training_pipeline
"""
use the best model to predict posted_rate in validation.csv/ fill the template’s predicted_rate column and save the completed file as 
validation_predictions.csv
"""
python -m src.predictions.predict_validation

"""
# this is a full pipilene(cleaning and training using data_pipeline and training_pipeline ) to get the best trained model to predict december data
"""
python -m src.pipelines.december_pipeline

# use the best model to predict predicted_rate in vdecember-chart-inputs.csv 
python -m src.predictions.predict_december

python score.py --predictions validation_predictions.csv --december-predictions data/december_chart_inputs.csv
```
