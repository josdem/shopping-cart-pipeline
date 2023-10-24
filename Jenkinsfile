#!/usr/bin/env groovy
pipeline {
  agent any
  stages {
    stage('Stopping') {
      steps {
        echo 'Stop shopping cart service'
        sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/stop-shopping.sh"'
        echo 'Done!'
      }
    }
    stage ('Build shopping cart service job') {
      steps {
        echo 'Starting Build Job'
        build job: 'shopping-cart-service'
        echo 'Done!'
      }
    }
    stage('Moving') {
      steps {
        echo 'Move shopping cart service'
        sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/move-shopping.sh"'
        echo 'Done!'
      }
    }
    stage('Starting') {
      steps {
        echo 'Starting shopping cart service'
        sh 'ssh josdem@jmailer.josdem.io "/home/josdem/deploys/start-shopping.sh"'
        echo 'Done!'
      }
    }
  }
}
