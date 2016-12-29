# zim SDK for JavaScript

## Overview

This SDK contains wapper code used to communicate with zim service.


## Getting started

1. Add script `<script data-main="scripts/main" src="scripts/require.js"></script>` to html page.
2. Edit script/main.js.

## Configuration

    var options = {appid: '',
        userid: '',
        authToken: '',
        onLogin: function(){},
        onClose: function(){},
        onMessage: function() {
            return true;
    }};

## Usage

    require(["zim"], function(zim) {
        var sdk = zim.SDK.getInstance();
        var rest = zim.Rest.getInstance();

        var options = {appid: 'test',
            userid: 'zhangpeihao@test',
            authToken: '875f27edf68d4d79adf1e803a891ae2e'};

        sdk.setOptions(options);

        sdk.startUpVoice(function() {
            // OnRegistered callback

            // now make a call to sid
            sdk.makeCallToSid("552888afafd129390300f9fe");
        }, function() {
            // OnDisconnected
        }, function(sid) {
            // OnIncoming callback

            // answer the incoming call
            sdk.answerCall();
        });

        sdk.startIM(function() {

        });

        // send message to server
        sdk.sendMessage({
            message: "{"":""}",
            timestamp: new Date(),
            type: "text/plain",
            fsid: options.ssid
        }, "54e05211afd12909af009c5c");

    });