for i in $(oc get projects  | grep Terminating| awk '{print $1}'); do echo $i; oc get serviceinstance -n $i -o yaml | sed "/kubernetes-incubator/d"| oc apply -f - ; done
