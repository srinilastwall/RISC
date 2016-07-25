![Lastwall Logo](lw-logo.jpg) 
# LastWall RISC - Risk based Authentication Firewall

The LastWall Authentiation Firewall system provides a javascript embeddable in your appropriate page.  The authentication fields, that need to be risk-evaluated are enabled via the script hooks. On submit, the script connects to the LastWall API and returns the trust value / the risk score associated with the username / password combination. Based on browser data, the API intelligently creates and assigns appropriate device profiles to the user. One user might have multiple devices profiles etc.

## Overview

An embeddable javascript is provided.  It needs to be initialized appropriately with the API key and Authorization Token. The API url needs to be set appropriately based on whether, the usage is for testing, development (sandbox) or production needs.

## Script Usage

The script is placed in the webpage which has the login action. Ideally the data collected by the script, is collected by a server-side program and then a API call made from the server-side as part of the authentication workflow.

## API usage

See [Integration] (Integration.md) for details of accessing the API from a server-side module.

## API Key

The API Key shall be provided by email.

## Authorisation Token

The Authorisation token shall be provided by email.


## URL for RISC Script

The current URL for the RISC script shall be provided by email.
