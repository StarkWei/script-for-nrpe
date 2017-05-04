#!/bin/bash

function usage() {
    local prog="${1:-check_closewait}"
    echo "Usage: $prog -h";
    echo "      Print this help and exit"
    echo "Usage: $prog -w <amount> -c <amount>";
    echo "       -w          the warning threshold amount current/max"
    echo "       -c          the critical threshold amount current/max"
}


while getopts "s:w:c:h" OPT;
do
        case $OPT in
                s)
                        STATUS=$OPTARG;;
                w)
                        WARNING=$OPTARG;;
                c)
                        CRITICAL=$OPTARG;;
                h)
                        usage $0
                        exit 3;;
        esac
done

if [ -z "$STATUS" -a -z "$WARNING" -a -z "$CRITICAL" ] ; then
        echo "Syntax error !!,Please refer to the help below"
        echo " "
        usage $0
        exit 3
fi

if [ -n "$STATUS" -a -z "$WARNING" ] ; then
        echo "Syntax error !!,Please refer to the help below"
        echo " "
        usage $0
        exit 3
fi
if [ -n "$STATUS" -a -z "$CRITICAL" ] ; then
        echo "Syntax error !!,Please refer to the help below"
        echo " "
        usage $0
        exit 3
fi

if [ -z "$STATUS" -a -n "$WARNING" ] ; then
        echo "Syntax error !!,Please refer to the help below"
        echo " "
        usage $0
        exit 3
fi

if [ -z "$STATUS" -a -n "$CRITICAL" ] ; then
        echo "Syntax error !!,Please refer to the help below"
        echo " "
        usage $0
        exit 3
fi

TMPSTATUS="/usr/local/nagios/libexec/status.log"
STATUSAMOUNT=`netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}' | grep $STATUS | awk '{print $2}' > $TMPSTATUS`
STATUSNM=`cat /usr/local/nagios/libexec/status.log`

if [ ! -n "$STATUSNM"  ]; then
         STATUSNM=0
         echo "OK: $STATUS is $STATUSNM"
         exit 0

elif [ $STATUSNM -ge $CRITICAL ]; then
        echo "CRITICAL: $STATUS is $STATUSNM"
        exit 2

elif  [ $STATUSNM -ge $WARNING ]; then
        echo "WARNING: $STATUS is $STATUSNM"
        exit 1

else
       echo "OK: $STATUS is $STATUSNM"
       exit 0
fi
