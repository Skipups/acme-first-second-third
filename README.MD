//READ
<html>
  <head>
    <style>
    .user {
      border: solid 1px black;
      padding: 1rem;
      margin: 1rem;
    }

    .favorite {
      background-color: tomato;
    }
    </style>
  </head>
  <body>
    <h1>Set Favorites</h1>
    <ul id='list'>
    </ul>
  <script>
    const users = [
      { name: 'moe' },
      { name: 'larry', isFavorite: true },
      { name: 'curly' },
      { name: 'shep' }
    ];

    const list = document.querySelector('#list');

    list.addEventListener('click', (ev)=> {
      if(ev.target.tagName === 'LI'){
        const idx = [...ev.target.parentNode.children].indexOf(ev.target);
        const user = users[idx];
        if(!user.isFavorite && users.filter( user => user.isFavorite).length === 3){
          alert('you must remove a favorite first');
        }
        else {
          user.isFavorite = !user.isFavorite;
          render();
        }
      }
    });

    const render = ()=> {
      const html = users.map(user => `<li class='user${ user.isFavorite ? ' favorite' : ''}'>${ user.name }</li>`).join('');
      console.log(html);
      list.innerHTML = html;
    };
    render();

  </script>
  </body>
</html>