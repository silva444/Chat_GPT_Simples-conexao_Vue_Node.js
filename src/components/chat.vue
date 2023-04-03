<template>
  <div class="container">

    <input type="text" v-model="input" name="texto" id="texto_id" placeholder="digite o texto">
    <p v-for="(text, index) in  texts" :key="index">
      {{ text }}
    </p>
    <button @click="get_open_ai">Enviar</button>

  </div>
</template>

<script>
import axios from 'axios';
import { Configuration, OpenAIApi } from "openai";


export default {
  name: 'chat',
  data() {

    return {
      input: '',
      texts: [],
    }
  },
  created() {



  },
  methods: {

    async get_open_ai() {
      //       const api_key = "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"
      // const configuration = new Configuration({
      //     organization: "org-xIMv7FApuSHCr7X8T5vWZN5d",
      //     apiKey: "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",
      // });
      // const openai = new OpenAIApi(configuration);
      // const response = await openai.listEngines();
      //       const axios = require("axios");

      //       const http = axios.create({
      //         headers: {
      //           "Content-Type": 'application/json',
      //           "Authorization": "Bearer" + api_key

      //         },
      //       })
      //       const param = {
      //   prompt: "How are you?",
      //   model: "text-davinci-003",
      //   max_tokens: 10,
      //   temperature: 0,
      // };

      //   http.post("https://api.openai.com/v1/models", param)
      //   .then((result) => {
      //     console.log(result.data.choices[0].text);
      //   })
      //   .catch((err) => {
      //     console.log(err);
      //   });

      const { Configuration, OpenAIApi } = require("openai");

const configuration = new Configuration({
  apiKey: "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",
});
const openai = new OpenAIApi(configuration);

try {
  const completion = await openai.createCompletion({
    model: "text-davinci-003",
    prompt: "Hello world",
  });
  console.log(completion.data.choices[0].text);
} catch (error) {
  if (error.response) {
    console.log(error.response.status);
    console.log(error.response.data);
  } else {
    console.log(error.message);
  }
}
//console.log(completion.data.choices[0].text);


      
    }
  }



  // async get_open_ai(){
  //   const axios = require("axios");
  //  const API_KEY= "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"
  // const APIBody = {
  //     "model": "gpt-3.5-turbo",
  //     "prompt": "What is the sentiment of this tweet? ",
  //     "temperature": 1,
  //     "max_tokens": 200,
  //     "top_p": 1.0,
  //     "frequency_penalty": 0.0,
  //     "presence_penalty": 0.0
  //   }

  //   await fetch("https://api.openai.com/v1/chat/completions", {
  //     method: "POST",
  //     headers: {
  //       "Content-Type": "application/json",
  //       "Authorization": "Bearer " + API_KEY
  //     },
  //     body: JSON.stringify(APIBody)
  //   }).then((data) => {
  //     return data.json();
  //   }).then((data) => {
  //     console.log(data);
  //     setSentiment(data.choices[0].text.trim()); // Positive or negative
  //   });
  // }


  // }

}
</script>

<style></style>