FISH-Decentralized-FIle-SHaring
===============================

FISH--FIle-SHaring
==================

FISH: FIle SHaring, a Distributed File System

"Truth is out there"

'FISH' is a file sharing system allowing its users to share media files (such as MP3 and images) on the Internet. Since it has been started, it has known a huge success, in such an extent that some universities have been forced to forbid their students to use FISH on their networks.

You may have recently heard or read about FISH since the trial it lost against some music publishing companies have been one of last summer's success story. Have you already wondered how such a system can work?

The Architecture: 
===
Decentralised P2P system
The Client-Server Architecture (which you can find here: https://github.com/thecodingguy/FISH-Centralized-FIle-SHaring) is based on a centralized management that has a disadvantage: the server can get overloaded and become a bottleneck, as the number of clients increases.

An alternative design is to remove the need for a centralized server by using "multicast" (or a distributed discovery algorithm) among clients (peers is this case), i.e. to build a P2P system. In this new design, each client (peer) possesses a directory listing the files the peer is sharing. 

To search for a file specified by the User, the peer should send a search request to (all) other peer. Below we describe an IP-multicast-based design. Note that IP multicast might not available (supported) in the network to which your computer is connected (especially in a wireless network). If it is the case, you should consider developing of a file search distributed algorithm in a unstructured P2P network of file sharing peers that communicate using TCP connections. In the case of using IP multicast, when starting, a peer registers itself to a 'file sharing' multicast group to which all search queries are sent. 

Each peer has a thread listening for queries and searching the peer's directory for a matching file. If a matching file is found, the peer replies directly to the requester. Later on, if the requesting peer decides to download the file, it connects to the peer providing the file and fetches it. Note again that IP multicast might not be supported in the network that your computer is connected to (especially in a wireless network).

P.S. A document that might be useful:  A draft of the Gnutella protocol specification: http://www.it.kth.se/courses/ID2212/assignments/FISH/gnutella_protocol_0.4.pdf (in PDF)
