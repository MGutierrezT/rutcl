# rutcl

Package para validar, limpiar, obtener dígito verificador y dar formato al RUT

```js
const { validate, clean, format, getDigit } = require('rut.js')

/**
 * Validar un RUT
 */

// true
validate('20.288.020-7')
validate('20288020-7')
validate('202880207')
validate('19.670.978-9')
validate('19670978-9')
validate('196709789')

// false
validate('20.288.020-0')
validate('20,288,020-7')
validate('20*288*020-7')
validate('20-288-020-7')
validate('error20.288.020-7')
validate('19670978-1')
validate('')
validate('0')
validate(0)

/**
 * Limpiar un RUT
 */

clean('202880207')      // '202880207'
clean('20.288.020-7')   // '202880207'
clean('19.670.978-1')   // '196709789'
clean('19*670*978-9')   // '196709789'
clean('000202880207')   // '202880207'

/**
 * Dar formato a un RUT
 */

format('20.288.020-7')  // '20.288.020-7'
format('20288020-7')     // '20.288.020-7'
format('19.670.978-9')  // '19.670.978-9'
format('196709789')     // '19.670.978-9'
format('20.288.020-7',{dots: false})  // '20288020-7'
format('20288020-7',{dots: false})     // '20288020-7'
format('19.670.978-9',{dots: false})  // '19670978-9'
format('196709789',{dots: false})     // '19670978-9'

/**
 * Obtener el dígito verificador de un RUT
 */

getDigit('20.288.020-7') // '7'
getDigit('20288020-7') // '7'
getDigit('202880207') // '7'
getDigit('19.670.978-9') // '9'
getDigit('19670978-9') // '9'
getDigit('196709789') // '9'
```

## Instalación

```bash
npm install --save rutcl
```

## Testing

```bash
npm install
npm test
```
