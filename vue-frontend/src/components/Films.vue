<template>
    <div class = "container">
            
            <h1 class = "text-center"> Films List</h1>

            <table class = "table table-striped">
                <thead>
                    <tr>
                        <th> Film Id</th>
                        <th> Film Id imdb</th>
                        <th> Film Nom</th>
                        <th> Film Url</th>
                    </tr>

                </thead>
                <tbody>
                    <tr v-for="film in films" v-bind:key="film.idImdb">
                        <td> {{film.id }}</td>
                        <td> {{film.idImdb }}</td>
                        <td> {{film.nom}}</td>    
                        <td> {{film.url}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
</template>

<script>

import FilmService from '../services/FilmService';

export default {
    name: 'Films_',
    data(){
        return {
            films: []
        }
    },
    methods: {
        getFilms(){
            FilmService.getFilms().then((response) => {
                this.films = response.data;   
            });
        }
    },
    created() {
        this.getFilms();
    }
}

</script>