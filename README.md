# Repository for final project
3a import requests
import json


def emotion_detector(text_to_analyse):
    url = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    headers = {
        "grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"
    }
    payload = {
        "raw_document": {
            "text": text_to_analyse
        }
    }

   
    response = requests.post(url, json=payload, headers=headers)
    formatted_response = json.loads(response.text)
    label = formatted_response['documenEmotion']['label']
    score = formatted_response['documentEmotion']['score']
    return {'label':label, 'score':score}

