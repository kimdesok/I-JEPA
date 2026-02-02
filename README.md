# I-JEPA demo script, aka, "PCam-JEPA"
## Methods & Materials
>* Frameworks: pytorch in Colab
>* Model: hugging face's "facebook/ijepa_vith14_1k" as a pretrained model
>* Datasets: hugging face's "1aurent/PatchCamelyon" as a train/test dataset representing breast cancer micrometastasis to lymphatic nodes in patches
>* (optional dataset: MHIST available upon a request at https://bmirds.github.io/MHIST/, representing colorectal polyps)
>* Tactics: <br>
            a. Visualyzing the Embeddings using t-sne <br>
            b. Performance comparison of Linear probe or Non-linear probe first and the end to end finetuning ('Deep_Full'). <br>
            c. Another performance comparison of Data Augmentation vs. no Data Augmentation <br>
            

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

>* End to end finetuning performance
-no data

--------------------------------------
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


>* **End to end finetuning performance with Data Augmentation**
--- Classification Report ---

              precision    recall  f1-score   support

       False       0.86      0.95      0.91     16391
        True       0.95      0.85      0.90     16377

    accuracy                           0.90     32768
   macro avg       0.91      0.90      0.90     32768 <br>
weighted avg       0.91      0.90      0.90     32768

ROC-AUC Score: 0.9659

<img width="666" height="547" alt="image" src="https://github.com/user-attachments/assets/95128b5f-f1c8-4c31-b2dc-f334623967e1" />

>* **End to end finetuning performance without Data Augmentation**
--- Classification Report ---

              precision    recall  f1-score   support

       False       0.81      0.96      0.88     16391
        True       0.95      0.77      0.85     16377

    accuracy                           0.86     32768
   macro avg       0.88      0.86      0.86     32768
weighted avg       0.88      0.86      0.86     32768

ROC-AUC Score: 0.9549

<img width="666" height="547" alt="image" src="https://github.com/user-attachments/assets/183f3c6d-a579-41d3-a433-87bb9bf2d0a9" />

### Discussion 
>* I-JEPA[1] has been known to be potentially learning the underlying biological structure without hand-crafted augmentations (like color jittering).  However in this preliminary work, the end to end finetuning without data augmentation showed a significantly less accuracy (0.86 vs. 0.90, no statistical test) compared to the one with data augmentation.  It is due to the fact that patchcamelyon is a specific domain dataset and somewhat limited in its scale.
>* Data augmentation is a still critical step to help generating the max. performance of I-JEPA models.
>* [Things to do] Explore the I-JEPA's performance with a dataset designed with a focus on a domain shift such as 'wltjr1007/Camelyon17-WILDS' available at HF with an extra label representing its origin institution.

### References
[1] Mahmoud Assran, Quentin Duval, Ishan Misra, Piotr Bojanowski, Pascal Vincent, Michael G. Rabbat, Yann LeCun, Nicolas Ballas, "Self-Supervised Learning from Images with a Joint-Embedding Predictive Architecture", CVPR 2023, available [here](https://www.semanticscholar.org/paper/Self-Supervised-Learning-from-Images-with-a-Assran-Duval/ee57e4d7a125f4ca8916284a857c3760d7d378d3?utm_source=direct_link)

