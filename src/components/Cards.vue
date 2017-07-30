<template lang="pug">
  .cards
    .card
      .card-title div Lorem ipsum dolor
      .card-article div div Lorem ipsum dolor sit amet, consectetur adipisicing elit. Corporis dolorem voluptatem esse, suscipit unde illum q ilorem
      .card-user somewant
      .card-date 2017/12/12
      .card-action
        button.btn Edit
        button.btn Revome
</template>
<style lang="sass" scoped>
  @import "./../base.sass"

  .cards
    width: 100%
    height: auto
    padding: 0px
    margin: 0px
    display: flex
    justify-content: space-around
    flex-wrap: wrap
    align-items: flex-start
    margin-top: 50px
    .card
      display: flex
      flex-direction: column
      background-color: $color-card
      width: calc(1000px / 3.1)
      min-height: 250px
      padding: 20px 10px 10px 10px
      margin-bottom: 10px
      border-top: 5px solid $color-secondary
      .card-title
        font-size: 1.5rem
        text-transform: uppercase
        color: $color-header
        font-weight: bold
        // text-align: center
        &::after
          content: ''
          display: block
          border: 5px solid $color-secondary
          width: 50px
          margin-top: 5px
      .card-article,.card-user,.card-action,.card-date
        // border: 1px solid #333
        margin-top: 10px
      .card-article
        flex: 1
      .card-user,.card-date
        text-align: right

      .btn
        color: $color-header
        padding: 5px 10px
        border: 1px solid $color-secondary
        transition: all 0.5s
        margin-right: 5px
        &:hover
          border: 1px solid rgba($color-secondary , 0)
          background-color: $color-secondary
          color: $color-card
</style>

