<template>

<p v-if="pending">Fetching...</p>
    <pre v-else-if="error">{{ error }}</pre>
    <pre v-else>Loaded</pre>

    <pre> {{ JSON.stringify(items.items[0].values, null, 2) }}</pre>

  <v-card
    :disabled="pending"
    :loading="pending"
    v-for="review in items.items"
    class="mx-auto my-12"
    max-width="374"
  >
    <template v-slot:loader="{ isActive }">
      <v-progress-linear
        :active="isActive"
        color="deep-purple"
        height="4"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-carousel height="250">
        <v-carousel-item v-for="(slide,i) in review['c-wToykWKGE4']"
            :src="slide.url"
            cover
        >
        
        <div class="text-h2">
              {{ slide }} Slide
            </div>
    
    </v-carousel-item>
    </v-carousel>   

    <!-- <v-img
      height="250"
      :src="review['c-wToykWKGE4'][0].url"
      cover
    ></v-img> -->

    <v-card-item>
      <v-card-title>{{ review.name }}</v-card-title>

      <v-card-subtitle>
        <span class="me-1">Local Favorite</span>

        <v-icon
          color="error"
          icon="mdi-fire-circle"
          size="small"
        ></v-icon>
      </v-card-subtitle>
    </v-card-item>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :model-value="review.values['c-ecfq4bRytZ']"
          color="amber"
          density="compact"
          size="small"
          half-increments
          readonly
        ></v-rating>

        <div class="text-grey ms-4">
          {{review.values['c-ecfq4bRytZ']}}/5
        </div>
      </v-row>

      <div class="my-4 text-subtitle-1">
        $ • Italian, Cafe
      </div>

      <div>Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating.</div>
    </v-card-text>

    <v-divider class="mx-4 mb-1"></v-divider>

    <v-card-title>Tonight's availability</v-card-title>

    <div class="px-4 mb-2">
      <v-chip-group v-model="selection" selected-class="bg-deep-purple-lighten-2">
        <v-chip>{{ review.values['c-eGd38cyLn7'] }}</v-chip>

        <v-chip>7:30PM</v-chip>

        <v-chip>8:00PM</v-chip>

        <v-chip>9:00PM</v-chip>
      </v-chip-group>
    </div>

    <v-card-actions>
      <v-btn
        color="deep-purple-lighten-2"
        text="Reserve"
        block
        border
        @click="reserve"
      ></v-btn>
    </v-card-actions>
  </v-card>

 


    <!-- <iframe src="https://coda.io/embed/KGZDix4HIW/_suZpE?hideSections=true" width=100% height=1000 style="max-width: 100%;" allow="fullscreen"></iframe> -->



</template>

<script setup>
    const authHeaders = { Authorization: `Bearer b87386ef-d655-411a-808a-cd70bd0bf9f3`}
    const {data: items, pending, error} = await useFetch('https://coda.io/apis/v1/docs/KGZDix4HIW/tables/Reviews/rows?valueFormat=rich', {
        headers: authHeaders
    })


    const test = [{"id":"i-q_3WhdAc9v","type":"row","href":"https://coda.io/apis/v1/docs/KGZDix4HIW/tables/grid-q1dVl0V46w/rows/i-q_3WhdAc9v","name":"La Española","index":2,"createdAt":"2024-02-08T16:00:59.462Z","updatedAt":"2024-02-08T16:02:21.462Z","browserLink":"https://coda.io/d/_dKGZDix4HIW#_tugrid-q1dVl0V46w/_rui-q_3WhdAc9v","values":{"c-QcnduFtkhv":"La Española","c-TpF4cLKSDJ":3,"c-yFEYg6JTPD":"CAFE","c-_MCxgMfUlz":"","c-wToykWKGE4":"1000202893.jpg,1000202894.jpg,1000202895.jpg","c-wBpYBsqRrE":"R$35","c--IfCvUOjqH":"","c-ecfq4bRytZ":3,"c-p5kFHWxOKR":1,"c-HLfa0LyMU0":"","c-4Q3RLIfESb":"2024-02-08T00:00:00.000-04:00","c-eGd38cyLn7":"Batata frita","c-a4ky53fUta":"Justificativas\nCarne e crosta: bem macia e igualmente cozida mas um pouco alta demais, o que rouba o sabor do molho. A crosta não estava bem presente  \nMolho e queijo: pouco molho e um pouco ácido demais. Queijo estava muito bom e trouxe um aroma sensacional\nAcompanhamentos: o purê um dos melhores que já comi mas somente ele não complementa o filé. \nConclusão\nO prato não ficou balanceado. Apesar de os ingredientes individualmente serem de ótima qualidade, o prato logo fica enjoativo. Não tinha crocância, o acompanhamento não equilibrava a carne com o molho ácido.  \nObservações do restaurante\nRestaurante: 4/5 \nAtendimento: 3/5 \nRapidez: 4/5\nCusto benefício: 2/5 \n\nO que signifcam as notas\n1/5 = ruim\n2/5 = abaixo da média\n3/5 = acima da média mas não pediria novamente\n4/5 = ótimo e voltaria pra pedir novamente\n5/5 = recomendado\n\nLembrando que não tenho nenhuma qualificação\nMetodologia 2024","c-EU2eAKQPna":"La Española","c-lTzg10cKKe":2024}},{"id":"i-9q9__EaCMp","type":"row","href":"https://coda.io/apis/v1/docs/KGZDix4HIW/tables/grid-q1dVl0V46w/rows/i-9q9__EaCMp","name":"Bella Parmegiana","index":1,"createdAt":"2024-01-13T03:08:38.839Z","updatedAt":"2024-02-08T16:08:01.117Z","browserLink":"https://coda.io/d/_dKGZDix4HIW#_tugrid-q1dVl0V46w/_rui-9q9__EaCMp","values":{"c-QcnduFtkhv":"Bella Parmegiana","c-TpF4cLKSDJ":4,"c-yFEYg6JTPD":"CAFE","c-_MCxgMfUlz":"","c-wToykWKGE4":"1000201432.jpg,1000201431.jpg,1000201430.jpg","c-wBpYBsqRrE":"R$60","c--IfCvUOjqH":"","c-ecfq4bRytZ":"","c-p5kFHWxOKR":1,"c-HLfa0LyMU0":"","c-4Q3RLIfESb":"2024-02-05T00:00:00.000-04:00","c-eGd38cyLn7":"Purê de batata","c-a4ky53fUta":"Justificativas\nCarne e crosta: bem macia e igualmente cozida mas um pouco alta demais, o que rouba o sabor do molho. A crosta não estava bem presente  \nMolho e queijo: pouco molho e um pouco ácido demais. Queijo estava muito bom e trouxe um aroma sensacional\nAcompanhamentos: o purê um dos melhores que já comi mas somente ele não complementa o filé. \nConclusão\nO prato não ficou balanceado. Apesar de os ingredientes individualmente serem de ótima qualidade, o prato logo fica enjoativo. Não tinha crocância, o acompanhamento não equilibrava a carne com o molho ácido.  \nObservações do restaurante\nRestaurante: 4/5 \nAtendimento: 3/5 \nRapidez: 4/5\nCusto benefício: 2/5 \n\nO que signifcam as notas\n1/5 = ruim\n2/5 = abaixo da média\n3/5 = acima da média mas não pediria novamente\n4/5 = ótimo e voltaria pra pedir novamente\n5/5 = recomendado\n\nLembrando que não tenho nenhuma qualificação\nMetodologia 2024","c-EU2eAKQPna":"Bella Parmegiana","c-lTzg10cKKe":2024}},{"id":"i-oSEKUp1k2g","type":"row","href":"https://coda.io/apis/v1/docs/KGZDix4HIW/tables/grid-q1dVl0V46w/rows/i-oSEKUp1k2g","name":"Farina","index":0,"createdAt":"2024-01-06T02:51:19.513Z","updatedAt":"2024-01-13T03:06:20.722Z","browserLink":"https://coda.io/d/_dKGZDix4HIW#_tugrid-q1dVl0V46w/_rui-oSEKUp1k2g","values":{"c-QcnduFtkhv":"Farina","c-TpF4cLKSDJ":2,"c-yFEYg6JTPD":2,"c-_MCxgMfUlz":"Restaurante: Farina\nNota sentimental: 2/5\nNota Técnica: 3/5\nValor: R$69\nPorção: 1 pessoa\nAcompanhamentos: Purê de batata\nData: 1/5/2024\n\nCarne e crosta: 2/5\nMolho e queijo: 3/5\nAcompanhamentos: 3/5\n\nJustificativas\nCarne e crosta: bem macia e igualmente cozida mas um pouco alta demais, o que rouba o sabor do molho. A crosta não estava bem presente  \nMolho e queijo: pouco molho e um pouco ácido demais. Queijo estava muito bom e trouxe um aroma sensacional\nAcompanhamentos: o purê um dos melhores que já comi mas somente ele não complementa o filé. \nConclusão\nO prato não ficou balanceado. Apesar de os ingredientes individualmente serem de ótima qualidade, o prato logo fica enjoativo. Não tinha crocância, o acompanhamento não equilibrava a carne com o molho ácido.  \nObservações do restaurante\nRestaurante: 4/5 \nAtendimento: 3/5 \nRapidez: 4/5\nCusto benefício: 2/5 \n\nO que signifcam as notas\n1/5 = ruim\n2/5 = abaixo da média\n3/5 = acima da média mas não pediria novamente\n4/5 = ótimo e voltaria pra pedir novamente\n5/5 = recomendado\n\nLembrando que não tenho nenhuma qualificação\nMetodologia 2024","c-wToykWKGE4":"1000182026.jpg,1000182023.jpg,1000182022.jpg","c-wBpYBsqRrE":"R$69","c--IfCvUOjqH":2.6666666666666665,"c-ecfq4bRytZ":3,"c-p5kFHWxOKR":1,"c-HLfa0LyMU0":3,"c-4Q3RLIfESb":"2024-01-05T00:00:00.000-04:00","c-eGd38cyLn7":"Purê de batata","c-a4ky53fUta":"Justificativas\nCarne e crosta: bem macia e igualmente cozida mas um pouco alta demais, o que rouba o sabor do molho. A crosta não estava bem presente  \nMolho e queijo: pouco molho e um pouco ácido demais. Queijo estava muito bom e trouxe um aroma sensacional\nAcompanhamentos: o purê um dos melhores que já comi mas somente ele não complementa o filé. \nConclusão\nO prato não ficou balanceado. Apesar de os ingredientes individualmente serem de ótima qualidade, o prato logo fica enjoativo. Não tinha crocância, o acompanhamento não equilibrava a carne com o molho ácido.  \nObservações do restaurante\nRestaurante: 4/5 \nAtendimento: 3/5 \nRapidez: 4/5\nCusto benefício: 2/5 \n\nO que signifcam as notas\n1/5 = ruim\n2/5 = abaixo da média\n3/5 = acima da média mas não pediria novamente\n4/5 = ótimo e voltaria pra pedir novamente\n5/5 = recomendado\n\nLembrando que não tenho nenhuma qualificação\nMetodologia 2024","c-EU2eAKQPna":"Farina","c-lTzg10cKKe":2024}}]

</script>