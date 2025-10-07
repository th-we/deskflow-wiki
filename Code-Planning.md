## Short Term Goals:
We want to finish these in the near future

1. Code Modernization and Cleanup, A lot of our code base is very old and needs updating, unused code paths should be removed and use of older methods should be updated. Our code base requires C++20 we should be using as many of those features as we can.  
1. Migrate platform specific code to use Qt where possible
    - QtDus in place of libportal for portals 
    - Qt classes in place of our in project created ones
    - Merge our event loop onto Qt

## Long Term Goals: 
 1.  separate the code into a set of common libraries that others can use to ensure compatibility and our own code that makes deskflow special. Other projects perhaps compositors would use this to add these features at a lower level or A display manager could for instance link the need items to allow connection to a server when before login. Deskflow and forks would ideally also use and develop these together.

