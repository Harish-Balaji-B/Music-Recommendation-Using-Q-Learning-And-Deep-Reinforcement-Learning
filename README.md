# Music Recommendation Using Q-Learning And Deep Reinforcement Learning

### Introduction
Music recommendation systems are crucial for providing personalized experiences in streaming platforms. Traditional approaches often rely on collaborative filtering or content based methods, which may not always capture the nuanced preferences of individual users. Reinforcement learning offers a powerful alternative by allowing the system to learn from user feedback and adapt its recommendations over time.

### Dataset
The music recommendation system was evaluated on a dataset comprising 228 unique artists and 7 different genres. Each song in the dataset was characterized by 17 features.

The dataset was carefully curated to encompass a diverse range of music styles and artist popularity, providing a realistic testbed for music recommendation algorithms. The use of this dataset allowed for an evaluation of how well the algorithms could learn from diverse musical preferences and recommend songs that align with a user’s specific tastes.

### Methodology
<strong>Q-Learning</strong>
* A Q-learning agent with a Q-table is used to learn optimal actions (like or dislike) based on the state representation of each track.
* The state representation is derived from a combination of GenreID, ArtistID, and TrackID, hashed to reduce the dimensionality.
* The agent learns from simulated user responses, rewarding actions that align with the user's preferred artist.
* The exploration probability balances exploration of new tracks with exploitation of learned preferences.
* The agent's q-table is updated using the Q-learning update rule, considering rewards and future potential rewards.

<strong>Deep Reinforcement Learning (Dueling DQN)</strong>
* A Dueling Deep Q-Network (DDQN) with two streams (value and advantage) is trained to learn the optimal policy.
* The input to the network is a preprocessed vector containing both numerical features (e.g., danceability) and one-hot encoded categorical features (e.g., genre, artist).
* The network learns to predict Q-values for each action (like or dislike), based on the current state.
* A replay buffer stores past experiences, allowing the network to learn from a diverse set of data.
* The target network is updated periodically to reduce oscillations during training.
* The agent explores the action space using an epsilon-greedy strategy.

### Why the Methodology
* <strong>Q-Learning: </strong> Relatively simple and computationally efficient, suitable for smaller datasets and exploring the impact of state representation.
* <strong>Deep Reinforcement Learning (Dueling DQN): </strong> More sophisticated approach that can handle complex, high-dimensional state spaces and potentially achieve better performance in large datasets.

### Reward
Both methods use a reward function to guide learning based on user preferences:
* <strong>Q-Learning: </strong> The reward is based on a combination of artist preference, genre preference, and danceability range.
* <strong>Deep Reinforcement Learning (Dueling DQN): </strong> The reward is based on a combination of artist preference, genre preference, and danceability range.

### Results
<strong>Q-Learning: </strong> 
* The agent learns to recommend songs by the preferred artist within the specified danceability range, but its performance is sensitive to the initial exploration rate and the chosen state representation.
* For 100 episodes – Loss trend over episodes:
