# I-JEPA demo script, aka, "PCam-JEPA"
## Methods & Materials
>* Frameworks: pytorch in Colab
>* Model: hugging face's "facebook/ijepa_vith14_1k" as a pretrained model
>* Datasets: hugging face's "1aurent/PatchCamelyon" as a train/test dataset representing breast cancer micrometastasis to lymphatic nodes in patches
>* (optional dataset: MHIST available upon a request at https://bmirds.github.io/MHIST/, representing colorectal polyps)
>* Tactics: a. Visualyzing the Embeddings
            b. Linear probe or Non-linear probe first and the end to end finetuning ('Deep_Full').

## Results
>* Visualization of Embeddings using t-sne<br>
<img width="989" height="790" alt="image" src="https://github.com/user-attachments/assets/5b59911b-cd69-4216-b843-ab972a424908" />
>* Linear probe performance <br>
--- Classification Report ---
precision    recall  f1-score   support

       False       0.84      0.83      0.84     16391
        True       0.83      0.84      0.84     16377

    accuracy                           0.84     32768
   macro avg       0.84      0.84      0.84     32768 <br>
weighted avg       0.84      0.84      0.84     32768
              

ROC-AUC Score: 0.9075
<img width="666" height="547" alt="image" src="https://github.com/user-attachments/assets/796398d4-5519-4218-88be-8cdcc0336819" />

>* Non-linear probe performance <br>
--- Classification Report ---

              precision    recall  f1-score   support

       False       0.78      0.90      0.84     16391
        True       0.88      0.75      0.81     16377

    accuracy                           0.82     32768 
   macro avg       0.83      0.82      0.82     32768 <br>
weighted avg       0.83      0.82      0.82     32768

ROC-AUC Score: 0.9152

<img width="666" height="547" alt="image" src="https://github.com/user-attachments/assets/2c7095f3-e205-4e79-8d2e-d94f1baf198a" />


>* End to end finetuning performance
--- Classification Report ---

              precision    recall  f1-score   support

       False       0.86      0.95      0.91     16391
        True       0.95      0.85      0.90     16377

    accuracy                           0.90     32768
   macro avg       0.91      0.90      0.90     32768 <br>
weighted avg       0.91      0.90      0.90     32768

ROC-AUC Score: 0.9659
<img width="666" height="547" alt="image" src="https://github.com/user-attachments/assets/95128b5f-f1c8-4c31-b2dc-f334623967e1" />





