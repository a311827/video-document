Configure Upstream
==================

You can change the upstream anytime on the distribution's **Configure/General** tab.

Upstream Groups
---------------

With **Upstream Groups**, it is possible to serve content from several origins and deliver them using one domain.


You can add additional upstreams in **Upstream Groups** on the **Configure/General** tab and reference them in edge rules on the **Rules/Edge Rules** tab.

.. _cache_revalidation:

Cache Revalidation Method
-------------------------

Edge servers must revalidate objects in their cache when the objects expire. On the **Configure / General** tab, you can select between two different methods for the edge servers to use.

Full Download
~~~~~~~~~~~~~

This is the default method which will work with all origins. With this method, when an object expires, the edge server will download a complete copy from your origin and cache the new copy. This method will always work, but it is not always very efficient, especially if the object has not changed.

Conditional Request
~~~~~~~~~~~~~~~~~~~

This method uses conditional requests with the "If-Modified-Since" header in order to identify if the content has changed on the origin. If it has not, the edge servers will revalidate the cached object without having to download a new copy of it. If the object has changed, the origin will send the new copy to the edge server.

In order for this method to work, your origin must support the "If-Modified-Since" header. Most modern HTTP servers now support this method. We recommend that you confirm that your origin supports it before enabling this feature. However, if your origin does not, the edge servers will fall back to **Full Download**.