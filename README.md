# interview-questions
 theoretical and practical questions


Q. how to pass the multiple api with same id 
ans:-
 const apiUrls = [
  'https://api.example.com/endpoint1',
  'https://api.example.com/endpoint2',
  'https://api.example.com/endpoint3',
  // ...more API endpoints
];

const commonId = '12345'; // Same ID to pass

const makeRequests = async () => {
  try {
    const responses = await Promise.all(
      apiUrls.map(url => fetch(`${url}?id=${commonId}`)) // Adding the ID to each request
    );

    const results = await Promise.all(responses.map(res => res.json()));
    console.log(results); // Handle the results from all APIs
  } catch (error) {
    console.error('Error in making requests:', error);
  }
};

makeRequests();

