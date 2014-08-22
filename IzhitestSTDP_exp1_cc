'''
Created on Jul 8, 2014

This is my method
The diffrerence with professor's model is the order of (V1-V2) or (V2-V1)
In this program, we simulate the chatting behaviour



@author: sun
'''
from IzhikevichClass import Izhike
import numpy as np
from matplotlib import pyplot as plt


NN=2
TotalTime=1000  # total Time
deltT= 0.25#0.25ms one step
#TotalSteps=np.arange(0,TotalTime+deltT,deltT)
#chattering =Izhike(0.1,0.2,-65,2.0)#simulate a Chattering neurons 

a0=0.02
b0=0.2
c0=-50
d0=2.0
ri=np.random.uniform(0,1)
#ri=0.0
a=a0+0.08*ri
b=b0-0.05*ri
chattering1 =Izhike(a,b,c0,d0)
ri=np.random.uniform(0,1)
#ri=0.1
a=a0+0.08*ri
b=b0-0.05*ri
chattering2 =Izhike(a,b,c0,d0)

#chattering neurons can fire stereotypical bursts of closely space spikes.
#I=5*np.random.randn()
#chattering2.I=8
#I=5
#print I

TotalSteps=np.arange(0,TotalTime,deltT)
#print TotalSteps
v0=-65
u0=0.2*v0
w=[0,0] #w[0] is the weght of A neuron to B, w[1] is the weight of B to A
Vsignal=np.zeros((NN,1))
Usignal=np.zeros((NN,1))
SynapticSpike1=[]
SynapticSpike2=[]
#print SynapticSpike
Vsignal[0,0]=v0
Usignal[0,0]=u0
chattering1.v=v0
chattering1.u=u0
chattering2.v=-10
chattering2.u=0.2*(-10)



for ts in TotalSteps[1:]:
    spikeflag1,spikeflag2=False,False 
    #False means now it is not the spike, True means now it is spike time
    #print ts
    #chattering.v=Vsignal[-1]
    #chattering.u=Usignal[-1]

    #print chattering.v
    '''
    if ts>=1 and ts<=100:
    #if ts==1:
        I=5
    else :
        
        I=(Vsignal[1,-1]-Vsignal[0,-1])*w[1]

    '''    
    I1=8
    inp1=0
    I=inp1+I1
    chattering1.v,chattering1.u,spikeflag1=chattering1.model(deltT,I=I1)
    #print chattering1.u
    Vsignal=np.insert(Vsignal,Vsignal.shape[1],chattering1.v,axis=1)
    #insert the v value after the last index of the numpy array
    Usignal=np.insert(Usignal,Usignal.shape[1],chattering1.u,axis=1)
    #print w[1];
    I2=8
    inp2=-(Vsignal[1,-2]-Vsignal[0,-2])*w[1] #electrical potential difference 
    I=inp2+I2    
    chattering2.v,chattering2.u,spikeflag2=chattering2.model(deltT,I)
    Vsignal[1,-1]=chattering2.v
    Usignal[1,-1]=chattering2.u
    #SynapticSpike1 is a list to store the spike time for the neuron 1

#print Vsignal.shape,TotalSteps.shape
#print SynapticSpike1
#print SynapticSpike2
#print np.corrcoef(Vsignal[0,],Vsignal[1,])
plt.plot(TotalSteps,Vsignal[0,])
plt.plot(TotalSteps,Vsignal[1,])
plt.show()
