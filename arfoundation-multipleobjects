//AR Foundation example code; making objects active only when image is tracked
//by 2021 Techlab St. Joost school of Art & Design

using System;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.XR.ARSubsystems;
using UnityEngine.XR.ARFoundation;

[RequireComponent(typeof(ARTrackedImageManager))]
public class Meerdereprefabs : MonoBehaviour {
    ARTrackedImageManager m_TrackedImageManager;
    GameObject obj1;
    GameObject obj2;

    void Awake() {
        m_TrackedImageManager = GetComponent<ARTrackedImageManager>();
    }
    void Start() {
        obj1 = GameObject.Find("augment-1");
        obj2 = GameObject.Find("augment-2");
        obj1.SetActive(false);
        obj2.SetActive(false);
    }

    void OnEnable() {
        m_TrackedImageManager.trackedImagesChanged += OnTrackedImagesChanged;
    }

    void OnDisable() {
        m_TrackedImageManager.trackedImagesChanged -= OnTrackedImagesChanged;
    }

    void OnTrackedImagesChanged(ARTrackedImagesChangedEventArgs eventArgs)
    {
        foreach (var trackedImage in eventArgs.updated)
        {
            if (trackedImage.trackingState == TrackingState.Tracking) {
                if (trackedImage.referenceImage.name=="image-1") obj1.SetActive(true);
                if (trackedImage.referenceImage.name=="image-2") obj2.SetActive(true);
            }
            else { //trackingstate = None or Limited
                if (trackedImage.referenceImage.name=="image-1") obj1.SetActive(false);
                if (trackedImage.referenceImage.name=="image-2") obj2.SetActive(false); 
            }
        }
    }    
}
