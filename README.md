<a name="readme-top"></a>

<br />
<div align="center">
  <h1 align="center">OpenVPN setup script</h1>
  <h5 align="center">Script that installs and configures OpenVPN Community server and creates tools to manage it</h5>
  <p align="center">
    <a href="https://github.com/benmotyka/openvpn-2fa-setup-script/issues">Report Bug</a>
    ·
    <a href="https://github.com/benmotyka/openvpn-2fa-setup-script/issues">Request Feature</a>
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#usage">Usage</a></li>
      </ul>
    </li>
    <li><a href="#common-problems">Common problems</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

This script installs and configures OpenVPN Community server and creates tools to manage it, such as:

- adding new user (username, password and Google Authenticator 2FA)
- removing existing user.

Script was adjusted specifically for Linux Rocky-8-ec2-8.5\*, x86_64 (on AWS) and its dependencies.

Based on the following repository: https://github.com/perfecto25/openvpn_2fa

<br />

## Getting Started

### Prerequisites

- [Linux Rocky-8-ec2-8.5*, x86_64 instance]

### Usage

1. Clone this repo
   ```sh
   git clone https://github.com/benmotyka/openvpn-2fa-setup-script.git
   ```
2. Install OpenVPN server:
   ```
    ./install.sh
   ```
3. Add first user
   ```sh
   ./manage.sh create john
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Common problems

**Issue** Can't import .ovpn file because of unknown dhcp-option
**Resolution**  Remove `dhcp-option DOMAIN-ROUTE .` line from client .ovpn file
<br/>

**Issue** Can't connect to server because of `TEST ROUTES: 0/0 succeeded len=-1 ret=0 a=0 u/d=down`, `Initialization Sequence Completed With Errors ( see http://openvpn.net/faq.html#dhcpclientserv )` connection logs
**Resolution**  Run below commands in cmd.exe as admin:
```
netsh winsock reset catalog
netsh int ipv4 reset reset.log
```

Add below line to client .ovpn file:

```
ip-win32 netsh
```
<br/>

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

Ben Motyka - [LinkedIn](https://www.linkedin.com/in/ben-motyka-97a729240/) - benmotykax@gmail.com

Project Link: [https://github.com/benmotyka/openvpn-2fa-setup-script](https://github.com/benmotyka/openvpn-2fa-setup-script)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
