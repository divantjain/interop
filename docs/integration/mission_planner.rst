Mission Planner Integration
===========================

The interoperability client library comes with a sample `Mission Planner
<http://ardupilot.org/planner/docs/mission-planner-overview.html>`__
integration example. This sample lives in `client/missionplanner
<https://github.com/auvsi-suas/interop/tree/master/client/missionplanner>`__
folder in the interoperability repository. This sample may serve as a core part
of a team's interoperability system or serve as an example use of the
interoperability client library.

This sample requires that the interoperability client ``interop`` module and
its dependencies are installed on the system and available in ``PYTHONPATH``.

There are two components to the Mission Planner integration:

`clientproxy.py
<https://github.com/auvsi-suas/interop/blob/master/client/missionplanner/clientproxy.py>`__
runs outside of Mission Planner and uses the interoperability client to send
data it receives from Mission Planner to the interoperability server.

`auvsi_mp.py
<https://github.com/auvsi-suas/interop/blob/master/client/missionplanner/auvsi_mp.py>`__
is run as a script inside of Mission Planner. It occasionally sends aircraft
telemetry to the client proxy, which in turn sends it to the interoperability
server.

Sample Invocation
-----------------

First, run ``clientproxy.py`` in a command prompt outside of Mission Planner,
passing it the URL of the interoperability server, your username, and your
password. (See ``clientproxy.py -h`` for invocation details)

.. code-block::

    > python clientproxy.py --url "http://192.168.1.5:8080" --username testuser --password testpass
    Use Control-C to exit

.. note::

    Verify that the URL you specify is accessible from your machine by
    attempting to open it in a web browser.

Inside Mission Planner, open the script console (under Actions in the Flight
Data panel) and paste the contents of ``auvsi_mp.py`` into the window. When you
close the window, the script will immediately start executing. It will print
the server info and then immediately begin communicating with the client proxy.
The client proxy will send telemetry to the interoperability server, and print
the rate at which it is doing so.
