Juvla

import socket
import typing

from termcolor import cprint
from nubia import argument, command, context

@command
@argument("hosts", description="Hostnames to resolve", aliases=["i"])
@argument("bad_name", name="nice", description="testing")
def lookup(hosts: typing.List[str], bad_name: int):
    """
    This will lookup the hostnames and print the corresponding IP addresses
    """
    ctx = context.get_context()
    print(f"hosts: {hosts}")
    cprint(f"Verbose? {ctx.verbose}")

    for host in hosts:
        cprint(f"{host} is {socket.gethostbyname(host)}")

    # optional, by default it's 0
    return 0




