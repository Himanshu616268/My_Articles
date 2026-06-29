Network packet analysis generates thousands of packets within seconds, making manual inspection difficult. Display filters in Wireshark help analysts focus only on the packets relevant to an investigation without modifying the captured data. Unlike capture filters, which determine which packets are recorded, display filters work on packets that have already been captured.
Steps for Applying Filters While Viewing

Step 1: Capture Network Traffic

  Before applying any filter Generate network activity such as: Opening websites, Sending ping requests, Accessing applications.
  Open Wireshark & Select the desired network interface.
  Click Start Capture.
  Stop the capture after sufficient traffic has been collected. The captured packets are now available for filtering.

Step 2: Locate the Display Filter Bar

  At the top of the Wireshark window is the Display Filter bar. This is where filter expressions are entered.
  As you type Green indicates a valid filter, Red indicates an invalid filter.
  This built-in validation helps identify syntax errors immediately.

Step 3: Apply a Simple Protocol Filter

  The easiest way to begin is by filtering a single protocol.
  Example: http(Displays only HTTP packets), dns, tcp, udp, icmp, arp. 
  Press Enter after typing the filter to apply it.

Step 4: Filter by IP Address

  Filtering by IP address helps isolate communication with a specific host.
  Source IP: ip.src == 10.0.2.15(Your own Displayed IP). Shows packets sent from the specified IP.
  Destination IP: ip.dst == 34.160.144.191. Shows packets sent to the specified destination.

Step 5: Filter by Port Number

  Applications commonly use well-known ports.
  Example: HTTP(tcp.port == 80), HTTPs(tcp.port == 443), DNS(udp.port == 53), SSH(tcp.port == 22).

Step 6: Combine Multiple Conditions

    Display filters support logical operators.
    AND: ip.addr == 192.168.1.5 && tcp. Shows TCP packets involving the specified IP address.
    OR: http || dns. Displays both HTTP and DNS traffic.
    NOT: !icmp. Hides ICMP packets from the display.
Step 7: Filter by Packet Fields

  Display filters can search individual protocol fields.
  HTTP Request Method: http.request.method == "GET".
  DNS Query Name: dns.qry.name == "example.com".
  TCP Flags: tcp.flags.syn == 1.

Step 8: Use Comparison Operators

Display filters support multiple comparison operators. These operators help identify packets based on size or field values.
Operator Purpose Example
==       Equal to tcp.port == 80
!=
Not equal
ip.addr != 192.168.1.10
>
Greater than
frame.len > 1000
<
Less than
frame.len < 100
>=
Greater than or equal
tcp.len >= 100
<=
Less than or equal
tcp.len <= 50
Step 9: Build Filters Using Packet Details

  Wireshark automatically generates the correct display filter. This method reduces syntax errors and speeds up analysis.
  Instead of memorizing syntax: Select a packet, Expand the protocol section, Right-click any field.
  Choose: Apply as Filter, Prepare as Filter.
  
Best Practices
  Capture all required traffic before filtering.
  Filter only the packets relevant to the investigation.
  Use packet field filtering for protocol-specific analysis.
  Validate results after applying each filter.
  Document important filter expressions for future reference.
