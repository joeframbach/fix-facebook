fix-facebook
============


    var blacklist = /pinterest|wedding|baby|football|steelers|hockey|sports|snow/;
    
    var home_stream = document.getElementById('home_stream');
    
    ​
    
    var testNode = function(node) {
    
    if (blacklist.test(node.innerHTML)) {
    
    home_stream.removeChild(node);
    
    }
    
    }
    
    ​
    
    MutationObserver = window.MutationObserver || window.WebKitMutationObserver;
    
    var observer = new MutationObserver(function(mutations, observer) {
    
    mutations.forEach(function(mutation) {
    
    Array.prototype.forEach.call(mutation.addedNodes, testNode);
    
    })
    
    }).observe(home_stream, {childList:true});

    Array.prototype.forEach.call(home_stream.childNodes, testNode);
