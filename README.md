
# HackPredictor-Deep
A deep learning system that facilitates the determination of the most feasible approach to emerge victorious in Hackathons. Visit the website at [HackPredictor.jnthn.uk](http://deephack.jnthn.uk).

![HackPredictor-Deep](/screenshot.png)

# What's this all about?
HackPredictor is a system founded on deep learning and big data analysis, aiming to examine the prevalent hackathon environment. It mainly focuses on large-scale data analysis based on more than sixty thousand 'hacks' on Devpost.

# Functioning
We utilized a web scraper to extract all hacks from Devpost and subsequently transformed the data into an extremely compact JSON. This Jason is imported into a Mongo database where we apply various methods for data analysis to discover correlations amongst distinctive data points. Our tensorflow model also processes the accumulated data. The model, which we have built, makes use of a triple input with 5 biases for computing what we term as a 'HackPredictor' score. This score aims to approximate the quantity of prizes a given hack may garner at a hackathon. At the moment, we have a prediction accuracy of approximately 75%, but we believe there is potential to boost it up to 84% without much hassle. However, managing big data demands a significant amount of time.

# Issues faced
Despite the hackathon proceeding smoothly, we encountered several hurdles related to the processing of big data. This includes pending over an hour for scrapers and parsers to execute their tasks and one of our processing servers consuming over 80GB of RAM at its peak.

# Run the Project
To initiate the project with the pre-existing data, you need to remove commenting from `mongo-seed` in `docker-compose.yml`. Execute `docker-compose up` and wait for the data to be entered into the database. Following this, stop docker and remove commenting from the `mongo-seed` image again. You are now equipped to execute the project with `docker-compose run`.

# Updating Data
The utility of the project is at its peak when using the most recent data. You will first need to download a copy of the latest projects. This can be done by executing the `dump.py` script located in the scraper directory, which should take around 2 hours. Afterwards, execute `parse_dump.py` to extract the latest data. This process takes approximately 20 minutes. You will be provided with a `devpostdump.json` file. Load this file into the MongoDB using the mongo-seed image. Please be cautious to avoid duplicating data and ensure dropping the database whenever you alter the data.