---
name: ml
description: Machine Learning skill - Algorithms, training, evaluation, deployment
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [train, evaluate, deploy, optimize, debug] }
    problem_type: { type: string, enum: [classification, regression, clustering, nlp, cv] }
  required: [task]

output_schema:
  type: object
  properties:
    code: { type: string }
    metrics: { type: object }
    recommendations: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 120000
---

# Machine Learning Skill

## PURPOSE
ML model development, training, and deployment.

## CORE COMPETENCIES
```
Algorithms:
├── Linear/Logistic Regression
├── Decision Trees, Random Forest
├── Gradient Boosting (XGBoost, LightGBM)
├── Neural Networks
└── Clustering (K-Means, DBSCAN)

Deep Learning:
├── CNNs (Computer Vision)
├── RNNs/LSTMs (Sequences)
├── Transformers (NLP)
├── Transfer Learning
└── Fine-tuning

MLOps:
├── Experiment tracking
├── Model registry
├── Feature stores
├── Model serving
└── Monitoring
```

## CODE PATTERNS

### Training Pipeline
```python
import mlflow
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, f1_score

with mlflow.start_run():
    # Split data
    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.2, random_state=42
    )

    # Train
    model = RandomForestClassifier(n_estimators=100)
    model.fit(X_train, y_train)

    # Evaluate
    predictions = model.predict(X_test)
    accuracy = accuracy_score(y_test, predictions)
    f1 = f1_score(y_test, predictions, average='weighted')

    # Log
    mlflow.log_params({"n_estimators": 100})
    mlflow.log_metrics({"accuracy": accuracy, "f1": f1})
    mlflow.sklearn.log_model(model, "model")
```

### PyTorch Training Loop
```python
for epoch in range(epochs):
    model.train()
    for batch in train_loader:
        optimizer.zero_grad()
        outputs = model(batch['input'])
        loss = criterion(outputs, batch['target'])
        loss.backward()
        optimizer.step()

    # Validation
    model.eval()
    with torch.no_grad():
        val_loss = evaluate(model, val_loader)

    scheduler.step(val_loss)
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Overfitting | Model too complex | Regularization, more data |
| Underfitting | Model too simple | More features, complexity |
| Slow training | Large data | GPU, batch size, mixed precision |
| OOM | Batch too large | Reduce batch, gradient accumulation |

## METRICS
```
Classification: Accuracy, Precision, Recall, F1, AUC-ROC
Regression: MSE, RMSE, MAE, R²
Ranking: MRR, NDCG
NLP: BLEU, ROUGE, Perplexity
```
