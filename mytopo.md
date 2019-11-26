from mininet.topo import Topo
from mininet.net import Mininet

class mytopo(Topo):
  def __init__(self):
   Topo.__init__(self)

   h1=self.addHost('h1', ip="10.0.1.100/24", defaultRoute="via 10.0.1.1")
   h2=self.addHost('h2', ip="10.0.2.100/24", defaultRoute="via 10.0.2.1")
   h3=self.addHost('h3', ip="10.0.3.100/24", defaultRoute="via 10.0.3.1")
   s1=self.addSwitch('s1')

   self.addLink(s1, h1)
   self.addLink(s1, h2)
   self.addLink(s1, h3)
   self.addLink(s1, h1, intfName2="s1-eth1", params2={"ip":"10.0.1.1/24"})
   self.addLink(s1, h2, intfName2="s1-eth2", params2={"ip":"10.0.2.1/24"})
   self.addLink(s1, h3, intfName2="s1-eth3", params2={"ip":"10.0.3.1/24"})

topos={ 'mytopo': (lambda: mytopo()) }
