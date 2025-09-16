# MKE4 + Kairos

## how to use
 - Pull a generic kairos image such as https://github.com/kairos-io/kairos/releases/download/v3.5.3/kairos-rocky-9.6-core-amd64-generic-v3.5.3.iso
 - boot system from iso
 - 8080 will be exposed on the host browse to it
 - paste in kairos.yaml
*make sure to include the #cloud-config comment header - it is required*
 - once all nodes have kairos installed - update mke4.yaml with the proper ssh config
 - mkectl apply -f mke4.yaml
 - ???
 - profit
