# UVM callback

## how to define a callback

1. define a callback class A_cb, which extends from the uvm_callback
2. in this callback class, define the virtual task or function that will be used in the component/object class A 
3. in the class A, use the macro `uvm_register_cb to pair the A and A_cb and put this pair into the class uvm_callbacks #(A, A_cb) 
4. in the class A, use the macro `uvm_do_callbacks macro to call the intended tasks and functions in all cb, which are added into the A_cb pool, uvm_callbacks #(A, A_cb)

## how to use a callback 

1. define a class A_cb_ext, which extends from the A_cb, and override the virtual task or  function 
2. Use the uvm_callbacks(A,A_cb)::add/add_by_name add the handle of the A_cb_ext into the instance(s) of A 

## show me the code 

```verilog
// show me the code here
class A_cb extends uvm_callback;
endclass

class A extends uvm_component;
  `uvm_register_cb(A, A_cb)
  
  //***
  `uvm_do_callbacks(A, A_cb, task_inside_A_cb)
  //***
  
endclass
```



