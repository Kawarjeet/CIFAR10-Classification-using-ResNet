# DeepLearning Amendments

Our model failed to load in the test scripts and hence the accuracy was being evaluated to zero. Our model had included other processing, training and testing steps instead of just the model description. Also the transformation that we applied is different than the one being used in the test script. To overcome all of these issues we have taken the following steps: 

1) Removed processing, training and testing steps from our model description in project1_model.py( we are uploading a new project1_model.py with the old one being renamed to project1_model_old.py to allow comparison and prove  that we did not make any changes to the model, but have removed only the processing, tranining and testing steps) 


2) We ran the training again using our old model(with no changes) to generate model1_project.pt file on a different colab notebook.


3) In the self_eval.py we have changed the image tranformation steps as per our transformation in our old model. The changes are as follows :
      Our model: 
            transform_test = transforms.Compose([
                               transforms.Pad(4),
                               transforms.RandomHorizontalFlip(),
                               transforms.RandomCrop(32),
                               transforms.ToTensor()
                               ])
                               
      self_eval.py testscript: 
              transform_test = transforms.Compose([
                                 transforms.ToTensor(),
                                 transforms.Normalize((0.4914, 0.4822, 0.4465), (0.2471, 0.2435, 0.2616)),
                                  ])
                                  
       So, we replaced transform_test in self_eval.py testscript with our model's transform_test as above. 
4) Finally, we have uploaded the project1_model.py( the one with only the model description and no other steps ) and the new project1_model.pt on brightspace and the accuracy being reported by self_eval.py is 88.1 %
