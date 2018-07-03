<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- <meta http-equiv="X-UA-Compatible" content="ie=edge"> -->
  <title>Document</title>

</head>

<body>
  <input type="text" placeholder="请输入4324" name="textOne" value="">
  <input type="password" placeholder="请输入密码">
  <input type="number" placeholder="请输入" name="textOne" value="">
  <script>
    window.onload = function () {
      if (!('placeholder' in document.createElement('input'))) {
        var input = Array.prototype.slice.call(document.querySelectorAll('[placeholder]'))
        input.forEach(function (m, x) {
          m.addEventListener('focus', function () {
            this.nextSibling.style.display = 'none'
          })
          m.addEventListener('blur', function () {
            if (!this.value) {
              this.style.display = 'none'
              this.nextSibling.style.display = 'inline'
            }
          })
          var inputClone = m.cloneNode()
          //密码框单独处理
          if (inputClone.getAttribute('type').toLowerCase() === 'password') {
            inputClone.setAttribute('type', 'text')
          }
          inputClone.setAttribute('value', inputClone.getAttribute('placeholder'))
          inputClone.style.display = 'none'
          m.insertAdjacentHTML('afterend', inputClone.outerHTML)
          m.nextSibling.addEventListener('focus', function () {
            this.style.display = 'none'
            this.previousSibling.style.display = 'inline'
            this.previousSibling.focus()
          })
          if (!m.value) {
            m.style.display = 'none'
            m.nextSibling.style.display = 'inline'
          }
        })
      }
    }
  </script>
</body>

</html>
