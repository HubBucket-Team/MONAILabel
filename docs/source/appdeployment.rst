======================
Application Deployment
======================

MONAI Label user apps are readily deployable on the MONAI Label Server. Simply, MONAI Label Server
opens a number of HTTP connection endpoints that define *what actions* clients can take, and in turn
the server relays the action to the MONAI Label application which defines *how the actions are taken*.

Deploying an Application
========================

The MONAI Label Server endpoints are available at startup. The user may download and start a sample app

.. code-block:: bash

  # download a sample app
  monailabel apps --name generic_deepedit --download --output .

  # start the sample app locally
  monailabel start_server --app generic_deepedit --studies <path/to/datastore>

and navigate to `http://127.0.0.1:8000/ <http://127.0.0.1:8000/>`_ on the browser (if the server
is running on the local machine). The user may choose to use the web UI to invoke the various endpoints
for the purpose of integration testing their labeling app.

The ``--studies`` argument may point to an empty folder or a folder with images in a flat structure.
If the datastore is empty the user is required to first upload an image (e.g. via 3DSlicer client or
web UI), however, if the datastore is populated the user may select the "next image" to annotate
based on the image selection strategy defined in the labeling app.

Application Call-flow
=====================

Figure 1 shows a typical call-flow between the client (e.g. 3DSlicer),
the MONAI Label Server, and the deployed MONAI Label application.

.. figure:: ../images/monai-server-application-callflow.svg
  :name: monai-server-application-callflow
  :alt: MONAI Server Application Call-flow

  **Figure 1:** MONAI Label Server relays endpoint requests to the MONAI Label App
  via the implemented methods in the API.
