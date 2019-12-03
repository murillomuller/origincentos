Baseado em: https://access.redhat.com/solutions/4220111

Crie um arquivo proxy_buffering.conf com o conteúdo:

    proxy_buffer_size          128k;
    proxy_buffers              4 256k;
    proxy_busy_buffers_size    256k;
    
Crie um ConfigMap através do arquivo:

    oc create configmap proxy-buffering --from-file={caminho-do-seu-arquivo}

Monte o volume através do ConfigMap:

    oc set volume dc/apicast-staging --add --name=proxy-buffering -m /opt/app-root/src/apicast.d/proxy_buffering.conf --sub-path=proxy_buffering.conf -t configmap --configmap-name=proxy-buffering
    oc set volume dc/apicast-production --add --name=proxy-buffering -m /opt/app-root/src/apicast.d/proxy_buffering.conf --sub-path=proxy_buffering.conf -t configmap --configmap-name=proxy-buffering
    
De um rollout para a última configuração

    oc rollout latest dc/apicast-staging
    oc rollout latest dc/apicast-production
    
