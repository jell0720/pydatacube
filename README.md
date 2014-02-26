# Python API for 'cube'-style data tables

WIP. Currently supports reading (subset of) JSONstat and
PC-Axis datasets and doing simple filtering for the data.
A simple example that shows most current functionality:

    import json
    import urllib2
    from pydatacube import jsonstat
    
    # Load jsonstat example data and pick a dataset
    # in it
    JSONSTAT_URL = "http://json-stat.org/samples/order.json"
    DATASET = 'order'
    data = json.load(urllib2.urlopen(JSONSTAT_URL))
    dataset = data[DATASET]
    
    # Convert to a pydatacube cube
    cube = jsonstat.to_cube(dataset)
    # Do some filtering
    subcube = cube.filter(A=("1", "2"), C="4")
    # And pretty printing
    for row in subcube:
        print("\t".join(map(str, row)))
    
