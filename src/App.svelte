<script>
  import Card from "./lib/Card.svelte";
  import '@material/web/button/filled-button.js'

  const cards = [
    {
      "title": "about me",
      "content": "Heya! I'm a full-stack developer who loves to code and learn new things. I've been a developer for about 3 years now and I'm currently learning Svelte and the Discord API :)<br><br>- seailz",
      "banner": "https://firebasestorage.googleapis.com/v0/b/seailz-pf.appspot.com/o/rwave.webp?alt=media&token=b14e8b7a-a1de-484a-9cfe-f323b7c4a2b3"
    },
    {
      "title": "discord.jar",
      "content": 'discord.jar is a Discord API wrapper for Java. It\'s currently a work in progress, but it\'s one of my main projects at the moment. It\'s open source and you can find it on my GitHub or by clicking this link: <a href="http://i.slz.lol/go/9S5zMI">http://i.slz.lol/go/9S5zMI</a>',
      "banner": "https://camo.githubusercontent.com/97bf12f8667a0db955d5d86ab7c09cd842632fbd9f96a5d3ef039ca1393e4fad/68747470733a2f2f63646e2e646973636f72646170702e636f6d2f6174746163686d656e74732f313034383931303836373132383932323137322f313036333832333430393338323935333034322f42697274686461795f5f315f2d72656d6f766562672d707265766965775f312e706e67"
    },
    {
      "title": "Chest Locking",
      "content": 'A simple Spigot plugin created to help users lock chests from griefers in Minecraft! You can find it here: <a href="http://i.slz.lol/go/ThD6GR">http://i.slz.lol/go/ThD6GR</a>',
      "banner": "https://firebasestorage.googleapis.com/v0/b/seailz-pf.appspot.com/o/chestlock.png?alt=media&token=04073566-45de-495a-b745-f7b8fb65c1a2"
    },
    {
      "title": "STU",
      "content":'A discord bot, REST API, and a websocket for a report system! Developed in Java using Spring & discord.jar. Includes session managing, rate limiting, and more! This was made in under 1 day. You can find it here: <a href="http://i.slz.lol/go/3uVCqJ">http://i.slz.lol/go/3uVCqJ</a>',
      "banner": "https://firebasestorage.googleapis.com/v0/b/seailz-pf.appspot.com/o/report.png?alt=media&token=172c6a43-ce48-413d-b6ee-6780317b3de4"
    }
    /*{
      "title": "Candor",
      "content": 'I currently manage Candor Services, and I developed the Discord bot that powers the server. It\'s one of my largest projects, and it includes the usage of the Discord API, Java, and AI! Check out Candor here: <a href="http://i.slz.lol/go/ryzHmX">http://i.slz.lol/go/ryzHmX</a>',
      "banner": "https://cdn.discordapp.com/attachments/970399585304461333/1088542883105218641/Frame_24.png",
      "thumbnail": "https://cdn.discordapp.com/attachments/970399585304461333/1050468410800222289/CANDOR_-_ICON_-_BLUE_ON_TRANS.png"
    }*/
  ]

  const cardIds = ["aboutme1", "djar", "chestLock", "stu"]
  
  /*
          transform: scale(0.3);
        width: 200px;
        margin-left: 400px;
        */


      
  var currentCard = ["aboutme1"]
  function transitionTo() {
    // Get index of current card in cardIds
    var cardId = currentCard[0];
    var cardIndex = cardIds.indexOf(cardId);
    // Get next card
    if (cardIndex + 1 > cardIds.length - 1) {
      cardId = cardIds[0];
    } else {
      cardId = cardIds[cardIndex + 1];
    }
    currentCard[0] = cardId;

    const cards = document.querySelectorAll(".card_container");
    cards.forEach(card => {
      if (card.id == cardId) {
        requestAnimationFrame(() => {
          card.style.transform = "scale(1)";
          card.style.marginLeft = "0px";
          // get parent
          var parent = card.parentElement;
          parent.style.zIndex = "4";
        })
        return;
      }
      requestAnimationFrame(() => {
        card.style.transform = "scale(0.3)";
        card.style.marginLeft = "600px";
        // get parent
        var parent = card.parentElement;
        var reversedCardIds = cardIds.slice().reverse();
        parent.style.zIndex = reversedCardIds.indexOf(card.id) + 1;
      })
    })
  }
</script>

<div class="container">
  <div class="header">
    <h1>my portfolio</h1>
  </div>

  <div class="card" style="z-index:3">
    <Card id="aboutme1" isAboutMeCard={true} title={cards[0].title} content={cards[0].content} image={cards[0].banner} />
  </div>
  <div class="card" style="z-index: 2">
    <Card id="djar" title={cards[1].title} content={cards[1].content} image={cards[1].banner} hasThumbnail={false} deselected={true}></Card>
  </div>
  <!--<div class="card" style="z-index: 1">
    <Card id="candor" title={cards[2].title} content={cards[2].content} image={cards[2].banner} hasThumbnail={true} deselected={true}></Card>
  </div>-->
  <div class="card" style="z-index: 1">
    <Card id="chestLock" title={cards[2].title} content={cards[2].content} image={cards[2].banner} hasThumbnail={false} deselected={true}></Card>
  </div>
  <div class="card" style="z-index: 0">
    <Card id="stu" title={cards[3].title} content={cards[3].content} image={cards[3].banner} hasThumbnail={false} deselected={true}></Card>
  </div>


  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <md-filled-button class="next_button" on:click={() => {
    transitionTo()
  }}><slot>Next Card</slot></md-filled-button>
  

  <div class="socials">
    <a href="https://www.github.com/seailz" target=”_blank”>
      <svg class="social" width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M24.0432 0.179932C10.8147 0.179932 0.0876465 11.0878 0.0876465 24.5445C0.0876465 35.3096 6.95165 44.4426 16.4699 47.6643C17.6671 47.8899 18.1067 47.1358 18.1067 46.4922C18.1067 45.9112 18.0845 43.9919 18.0742 41.956C11.4097 43.4299 10.0034 39.0812 10.0034 39.0812C8.9137 36.265 7.34358 35.5161 7.34358 35.5161C5.17009 34.0039 7.50742 34.035 7.50742 34.035C9.91297 34.2065 11.1796 36.5458 11.1796 36.5458C13.3162 40.2707 16.7837 39.1938 18.1507 38.5712C18.3657 36.9969 18.9866 35.9212 19.6716 35.3132C14.3508 34.6971 8.7574 32.6079 8.7574 23.2719C8.7574 20.6118 9.6932 18.4383 11.2256 16.732C10.9769 16.1179 10.1569 13.6402 11.4577 10.2841C11.4577 10.2841 13.4693 9.62928 18.0472 12.7816C19.9581 12.2418 22.0074 11.971 24.0432 11.9618C26.0791 11.971 28.13 12.2418 30.0444 12.7816C34.6167 9.62928 36.6256 10.2841 36.6256 10.2841C37.9295 13.6402 37.1091 16.1179 36.8604 16.732C38.3964 18.4383 39.3259 20.6118 39.3259 23.2719C39.3259 32.6301 33.7218 34.6906 28.3874 35.2938C29.2467 36.0499 30.0123 37.5327 30.0123 39.8059C30.0123 43.0655 29.9845 45.6893 29.9845 46.4922C29.9845 47.1406 30.4157 47.9003 31.63 47.6611C41.1431 44.4357 47.9984 35.3059 47.9984 24.5445C47.9984 11.0878 37.273 0.179932 24.0432 0.179932Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M9.16084 35.1623C9.10808 35.2837 8.92084 35.3196 8.75026 35.2365C8.57651 35.157 8.47892 34.992 8.53525 34.8706C8.58682 34.7459 8.77446 34.7116 8.94781 34.7943C9.12196 34.8742 9.22113 35.0408 9.16084 35.1623Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M10.1312 36.263C10.0169 36.3707 9.79356 36.3207 9.64203 36.1504C9.48533 35.9805 9.45598 35.7534 9.57181 35.644C9.68963 35.5363 9.90622 35.5867 10.0633 35.7566C10.22 35.9285 10.2506 36.154 10.1312 36.263Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M11.0757 37.6662C10.9289 37.7699 10.6889 37.6727 10.5405 37.456C10.3938 37.2394 10.3938 36.9795 10.5437 36.8754C10.6925 36.7713 10.9289 36.8649 11.0793 37.08C11.2256 37.2999 11.2256 37.5601 11.0757 37.6662Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M12.3697 39.0219C12.2384 39.1692 11.9587 39.1296 11.754 38.9287C11.5446 38.7322 11.4863 38.4534 11.618 38.3062C11.7509 38.1585 12.0321 38.2 12.2384 38.3994C12.4463 38.5954 12.5097 38.8763 12.3697 39.0219Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M14.1548 39.8091C14.0969 39.9999 13.8275 40.0867 13.5562 40.0056C13.2853 39.9221 13.1079 39.6985 13.1627 39.5057C13.219 39.3136 13.4896 39.2232 13.7629 39.31C14.0334 39.3931 14.2112 39.615 14.1548 39.8091Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M16.1153 39.9552C16.122 40.1561 15.8919 40.3227 15.6071 40.3259C15.3207 40.3328 15.089 40.1702 15.0859 39.9725C15.0859 39.7696 15.3108 39.6045 15.5972 39.5997C15.882 39.594 16.1153 39.7554 16.1153 39.9552Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M17.9397 39.6392C17.9738 39.8353 17.7758 40.0367 17.493 40.0899C17.2149 40.142 16.9575 40.0209 16.9222 39.8264C16.8876 39.6255 17.0892 39.4242 17.3669 39.3721C17.6501 39.3221 17.9036 39.4399 17.9397 39.6392Z" fill="white"/>
        </svg>
      </a>
      <a href="https://discord.com/users/947691195658797167" target=”_blank”>
        <svg class="social discord" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 127.14 96.36"><defs><style>.cls-1{fill:#fff;}</style></defs><g id="图层_2" data-name="图层 2"><g id="Discord_Logos" data-name="Discord Logos"><g id="Discord_Logo_-_Large_-_White" data-name="Discord Logo - Large - White"><path class="cls-1" d="M107.7,8.07A105.15,105.15,0,0,0,81.47,0a72.06,72.06,0,0,0-3.36,6.83A97.68,97.68,0,0,0,49,6.83,72.37,72.37,0,0,0,45.64,0,105.89,105.89,0,0,0,19.39,8.09C2.79,32.65-1.71,56.6.54,80.21h0A105.73,105.73,0,0,0,32.71,96.36,77.7,77.7,0,0,0,39.6,85.25a68.42,68.42,0,0,1-10.85-5.18c.91-.66,1.8-1.34,2.66-2a75.57,75.57,0,0,0,64.32,0c.87.71,1.76,1.39,2.66,2a68.68,68.68,0,0,1-10.87,5.19,77,77,0,0,0,6.89,11.1A105.25,105.25,0,0,0,126.6,80.22h0C129.24,52.84,122.09,29.11,107.7,8.07ZM42.45,65.69C36.18,65.69,31,60,31,53s5-12.74,11.43-12.74S54,46,53.89,53,48.84,65.69,42.45,65.69Zm42.24,0C78.41,65.69,73.25,60,73.25,53s5-12.74,11.44-12.74S96.23,46,96.12,53,91.08,65.69,84.69,65.69Z"/></g></g></g></svg>
      </a>
  </div>
</div>

<style>
  .socials {
    position: absolute;
    bottom: -3%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .social {
    width: 25px;
    margin-right: 10px;
  }

  .social.discord {
    margin-bottom: 13px;
  }


  .next_button {
    position: absolute;
    bottom: 10%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  @media (max-width: 768px) {
    .next_button {
      bottom: 5%;
    }
  }

  .container {
    background-color: rgb(32, 32, 32);
    width: 100%;
    height: 100%;
    overflow-x: hidden;
  }

  .header h1 {
    margin: 0px;
    color: white;
  }

  .card {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }


  .header {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>