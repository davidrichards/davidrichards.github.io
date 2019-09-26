---
layout: post
title:  Founder-Driven VC, Feature Engineering
summary: Notes from an interview with Keith Rabois and a micro course on Kaggle.
date:   2019-09-25-05:03:55
categories: raw
---
## Notes from Keith Rabois

Rabois found Peter Thiel smarter than most people at Stanford, as well as odder. Thiel thinks a couple steps ahead of everyone else. People didn't believe his intelligence would support business success, or that he'd be interested in business rather than politics or law. When Rabois met Thiel in the 80s and 90s, he did not understand what makes effective CEOs. Instead Rabois had a mental model from popular media of what a successful CEO does.

[Mehta, 2019]

### Intelligence

IQ doesn't correlate with successful entrepreneurs. Rather, it's connecting things that other people miss. All successful founders Rabois has met have IQs, but that isn't the only factor.

The characteristics that make successful founders is tied to the type of business they are building, what they are trying to accomplish, their merit, the value proposition the company offers, and the risks the company is taking.

[Mehta, 2019]

### Resourcefulness

Besides IQ, resourcefulness is a common trait. Paul Graham talks about being relentlessly resourceful. Successful founders assess people accurately, quickly, and can learn from that. Founders mostly hire people. Rabois sees technology startups more like sports teams, building the right team, getting the right people doing the right jobs and ensuring it stays that way.

[Mehta, 2019]

### Inborn Tenacity

Tenacity is something inborn, it doesn't come later in life. Do you accept excuses or do you prevail? Are you willing to be the best in all cases? Founders tell stories from their own life of tenacity, that's the best way to judge if it's there. Even people that have had relatively posh lives have challenged themselves if they have this tenacity. It shows up in competitive sports, school, coding competitions, or other competitions. Stress is important for their success. You can't take the leap with people that haven't been challenged or stressed.

[Mehta, 2019]

### Thesis Investment

Rabois invested in Peter Thiel in 2003. He did not use thesis investment. People are the key to Rabois' decisions.

There may be some false positives or false negatives, but overall, looking for significant leaders has guided Rabois.

Once he's picked his founder, he adjusts his role to what is missing. Founders might be product, technology, or sales-driven people. Founders might struggle to manage people. Rabois compliments what's going right at startup.

At LinkedIn, Rabois primarily focused on generating new revenue streams. This became job boards and recruiting. This means the venture capitalist must have a fairly wide skillset.

Working with founders, they have no patience. They speak succinctly. Fill in the dots. Accomplish their vision. Ensure the founder owns their own vision. They are implanting that on everyone around them. The VC is ensuring nothing goes wrong with that. Work on the acute areas of need, block and tackle their vision. 

Figure out your comparative advantage, invest in it, and improve.

[Mehta, 2019]

### Board Member

A good board member is like a good psychologist. Be there to let the founders and executive team talk to you, in order to clarify their thinking. It can look like the Socratic method. Ask questions until the executive team understands their own vision. Hold a mirror, but play it back in an exaggerated way, so it's clear what they want, what they don't want, and what's being lost in translation.

[Mehta, 2019]

### Lean Startup

Rabois disagrees with the Lean Startup, it's dump and a bankrupt philosophy for mediocre people with a mediocre vision and ambition. It minimizes the challenge of short term failure at the expense of the long term opportunity.

Startups are not bottom-up exercises.

The founder must paint a picture of a better world, and deliver it. Cast a movie around a vision, deliver that vision, and sell tickets. Deliver finished products. The customers, Jack at Square says, are not Guinea pigs.

[Mehta, 2019]

### Read More

Rabois invests in new and emerging technology every few weeks. He lets the founders lead and teach and plays the role of detective. Reading is also important. Read for your own knowledge, invest in your own learning. The most voracious readers are the most successful. Be intellectually curious. Read well-written material. Connect the dots between disciplines and fields.

Read The Upside of Stress, High Output Management, and Why We Sleep.

[Mehta, 2019]

### Create New Value

At LinkedIn, they had a long-tail search problem. Yelp had this same problem with restaurants. He followed Yelp's lead and created compelling and unique content for each person so Google would recognize it as such. 12-13 years later, if you search a person, their LinkedIn profile comes up. Because they are better at the SEO than Facebook, they have an increase of about 25-33% more usage. This became a value proposition that didn't exist before.

[Mehta, 2019]

### Founders Teach Execution

The founders Rabois has worked with have taught him better models of execution than the Lean methodology. A lot of these teams raised money on only a Keynote presentation and a strong team. Jack recognize that a phone is an always-on computer in everyone's pocket, and he executed on that vision. At Square, nobody knew how to find and market to micro businesses, but he figured it out.

[Mehta, 2019]

### Efficient Markets

The most important thing for finding successful companies is the talent. It must be combined under the same roof to create solutions. Venture hasn't changed a lot, it's fairly efficient, and it follows the talent. Outside of the US, there are places where VC is inefficient.

[Mehta, 2019]

### Future Opportunities

Generally speaking, Rabois is interested in healthcare and finance. He invests in the most ridiculous companies. His VC friends laugh at him. Without that, Rabois doesn't think he's taking enough risk.

[Mehta, 2019]

## Feature Engineering

In this micro-course, Mat Leonard teaches features engineering, including how to build a baseline model, encoding categorical features, generating new features, and selecting which features to use in a model. The TalkingData AdTracking competition on Kaggle is used to teach these principles.

[Leonard, 2019]

### Setup

Importing a dataframe and parsing dates, we begin to see how one dataset looks. In this case, we determine which column has outcomes, and how we might learn those outcomes. By looking at the categories for the outcomes using panda's unique function, and the count of each outcome using panda's groupby function, we discover the class imbalance in the data--a lot of failed, canceled, and successful outcomes, and a few live, suspended, and undefined outcomes. A clever query and assign prepares the dataset to have 1 for successful, and 0 otherwise.

[Leonard, 2019]

### Cleanup

Timestamps can be unpacked to hour, day, month, and year and assigned back to the dataframe. The LabelEncoder from sklearn.preprocessing converts categorical variables to numbers. A very simple approach to splitting the data works. Remember, this is a baseline model.

[Leonard, 2019]

### Baseline Model

For this example, LightGBM is used for a baseline model. It's very ast to train, and often provides the best performance, even compared to XGBoost. Using some default hyperparameters, a model is trained. Using sklearn's ROC AUC Score, the baseline model seems to perform fairly well.

[Leonard, 2019]


## References:

Leonard, M. (n.d.). Baseline Model. Retrieved September 25, 2019, from https://kaggle.com/matleonard/baseline-model

Mehta, K. (2019, September 25). Finding Genius: Keith Rabois, Founders Fund. Retrieved September 25, 2019, from Medium website: https://medium.com/@kmehta107/finding-genius-keith-rabois-founders-fund-d0a69b1f9e95


