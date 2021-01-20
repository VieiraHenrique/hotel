# EasyBooking

## Powered by FlowIQ.ai

---

This is a prototype for a hotel booking website where the user can search for hotels in a certain city, go through the list of hotels, see details for each hotel and finally select one to make a booking for.

The prototype is done in Vue.JS with the framework Nuxt.JS and can be found at this address : https://hotel-dusky.vercel.app/

The prototype presents three pages :

- LOGIN
- MAIN PAGE where the user search and display hotels
- DYNAMIC PAGE for the selected hotel, allowing the booking of the hotel in the specified time and price

---

### DESIGN CONSIDERATIONS

The design intends to attract the user attention towards the idea of holydays.

Every page emphasizes the hotel experience by showing pictures.

Due to that, the design is sober with mainly gray colors and the blue from the FlowIQ.ai logo.

This choice was made so the app doesn't become too crowded by the numerous colors from the many hotels pictures. These pictures are the one that will bring color to the app.

### LOGIN PAGE

The first page (login page) shows the name of the app, the engine on which the app runs (FlowIQ.ai) and the login informations.

It remembers the last login and asks if the user wants to continue connected or change to another account. It also allows a new user to register in case he/she has no account.

### MAIN PAGE

Beautiful pictures are used in the begining of the page to, again, emphasizes the feeling of holydays and pleasure.

Below that, we find an engine to make it easy to select the ciy and the dates we would like to book.

At the right, we find two opinions from other users regarding the tool.

Once the place and the dates are chosen, the first nine hotels are showned below.

Other pages cab be added, but once the first page is the most important one, this creates a new value to be negotiated with prospective hotels.

A message is displayed to te user inviting him to wait while the response is loading.

In case the user didn't provide any city and/or booking dates, he is alerted by a message as well.

Based on the quality aspect of the hotel presented, the user is invited to chose to explore one of them.

### DYNAMIC PAGE

Once a hotel is chosen, the user is presented with the name, place, number of stars and the main amenities included in the hotel.

Beside that, he can check the price per night, the chosen dates for check in and check out, total number of nights and total price.

Just below that, he has the option to do the booking.

Below all this data, the user can check special pictures from the hotel and what he/she can expect from his/her stay.

Clicking on a picture, a modal is opened with a larger picture
