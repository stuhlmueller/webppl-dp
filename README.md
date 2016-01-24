# webppl-dp

This package provides a function `dp.cache` that memoizes functions in a way compatible with mutual recursion.

    var even = dp.cache(function(x) {
      console.log('Called `even` with argument ' + x);
      if (x == 0) {
        return true;
      } else {
        return odd(x - 1);
      }
    });
    
    var odd = dp.cache(function(x) {
      console.log('Called `odd` with argument ' + x);
      if (x == 0) {
        return false;
      } else {
        return even(x - 1);
      }
    });
    
    console.log(odd(3));
    console.log(odd(5));

returns

    Called `odd` with argument 3
    Called `even` with argument 2
    Called `odd` with argument 1
    Called `even` with argument 0
    true
    Called `odd` with argument 5
    Called `even` with argument 4
    true

## Installation

To globally install `webppl-dp`, run:

    mkdir -p ~/.webppl
    npm install --prefix ~/.webppl webppl-dp

This may print warnings (`npm WARN ENOENT`...) which can be ignored.

To upgrade to the latest version, run:

    npm install --prefix ~/.webppl webppl-dp --force

## Usage

Once installed, you can make `dp.cache` available to `program.wppl` by running:

    webppl program.wppl --require webppl-dp

## License

MIT
