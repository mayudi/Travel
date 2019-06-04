<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities"
                   :hotCities="hotCities"
                   :letter="letter"
        ></city-list>
        <city-alphabet :cities="cities"
                       :letter="letter"
                       @change="handleLetterChange"
        ></city-alphabet>
    </div>
</template>

<script>
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('https://www.easy-mock.com/mock/5cf5d5b80a6c103663bf0623/city')
        .then(this.handleGetCityInfoSucc)
    },
    handleGetCityInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.hotCities = data.hotCities
        this.cities = data.cities
      }
    },
    handleLetterChange (letter) {
      this.letter = letter
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>
