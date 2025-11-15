# Saving-animals-bot
A bot to spread awareness about the animal rescue I do and encourage people to donate to help me save more animals

import tweepy
import time
import random

# Twitter API credentials - YOU WILL FILL THESE IN LATER
API_KEY = "C0Cd8BIjLAnBRHZzvTfGxJ3E7"
API_SECRET = "msL4mzzIdnpHjmwD2xuyhsosDxIVSxN50bFYxgyQE3W4taSGHY"
ACCESS_TOKEN = "220339465-Tcf0rypXCRXHQD0mm71s6LPzjjQLrHHU4yTpevMF"
ACCESS_TOKEN_SECRET = "hacXFuNlcPJ6QiHfUDsbTcSQ9mW2ENesFq7D78Hvl9Vb0"

# Messages about animal rescue (customize these!)
MESSAGES = [
    "🐾 Every animal deserves a loving home. Help us save more lives! Donate today: [YOUR_DONATION_LINK] #AnimalRescue #SaveAnimals",
    "🐕 We rescued 5 dogs this week, but there are so many more waiting. Your donation makes a difference! [YOUR_DONATION_LINK] #RescueDogs",
    "🐱 Cats need love too! Support our mission to rescue and rehome animals in need. [YOUR_DONATION_LINK] #CatRescue #AdoptDontShop",
    "❤️ Behind every rescue is a story of hope. Help us write more happy endings! Donate: [YOUR_DONATION_LINK] #AnimalWelfare",
    "🏠 A small donation can give an animal a second chance at life. Every dollar counts! [YOUR_DONATION_LINK] #RescueAnimals",
    "🐾 Did you know? Your support helps us provide food, shelter, and medical care to abandoned animals. [YOUR_DONATION_LINK] #AnimalRescue",
]

def post_tweet():
    """Post a random message from the MESSAGES list"""
    try:
        # Authenticate with Twitter
        auth = tweepy.OAuthHandler(API_KEY, API_SECRET)
        auth.set_access_token(ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
        api = tweepy.API(auth)
        
        # Select a random message
        message = random.choice(MESSAGES)
        
        # Post the tweet
        api.update_status(message)
        print(f"Tweet posted successfully: {message}")
        
    except Exception as e:
        print(f"Error posting tweet: {e}")

def run_bot():
    """Run the bot continuously"""
    print("Animal Rescue Bot started!")
    print("Posting tweets every 4 hours...")
    
    while True:
        post_tweet()
        # Wait 4 hours (14400 seconds) before next tweet
        # You can adjust this timing
        time.sleep(14400)

if __name__ == "__main__":
    run_bot()

