===================
Sharing CUDA Memory
===================

.. cuda-deprecated::

.. _cuda-ipc-memory:

Sharing between process
=======================

Sharing between processes is implemented using the Legacy CUDA IPC API
(functions whose names begin with ``cuIpc``), and is supported only on Linux.


Export device array to another process
--------------------------------------

A device array can be shared with another process in the same machine using
the CUDA IPC API.  To do so, use the ``.get_ipc_handle()`` method on the device
array to get a ``IpcArrayHandle`` object, which can be transferred to another
process.


.. automethod:: numba.cuda.cudadrv.devicearray.DeviceNDArray.get_ipc_handle
    :noindex:

.. autoclass:: numba.cuda.cudadrv.devicearray.IpcArrayHandle
    :members: open, close


Import IPC memory from another process
--------------------------------------

The following function is used to open IPC handle from another process
as a device array.

.. automethod:: numba.cuda.open_ipc_array
