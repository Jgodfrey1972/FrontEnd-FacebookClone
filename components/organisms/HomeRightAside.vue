<template>
  <Aside>
    <div class="content">
      <h3 class="aside-title">Contatos</h3>

      <div class="contacts-wrapper">
        <span class="status-title">Online</span>

        <ul class="contacts">
          <Contact
            image-u-r-l="profile-pic.png"
            username="Rafael Barros"
            :link="'RafaelBarros'"
            status="online"
          />
          <Contact
            image-u-r-l="profile-pic.png"
            username="Gabriel Rocha Melo"
            :link="'GabrielRochaMelo'"
            status="busy"
          />
          <Contact
            image-u-r-l="profile-pic.png"
            username="Stephanie Mota"
            :link="'StephanieMota'"
            status="online"
          />
          <Contact
            image-u-r-l="profile-pic.png"
            username="Alexandre Mendes"
            :link="'AlexandreMendes'"
            status="busy"
          />
        </ul>

        <span class="status-title">Offline</span>

        <ul class="contacts">
          <Contact
            image-u-r-l="profile-pic.png"
            username="Deborah Gomes"
            :link="'DeborahGomes'"
            status="offline"
          />
          <Contact
            image-u-r-l="profile-pic.png"
            username="Jéssica Soares"
            :link="'JéssicaSoares'"
            status="offline"
          />
          <Contact
            image-u-r-l="profile-pic.png"
            username="Chris Nathaniel"
            :link="'ChrisNathaniel'"
            status="offline"
          />
        </ul>
      </div>
    </div>
  </Aside>
</template>

<style lang="scss" scoped>
.aside {
  @include screen('small') {
    display: none;
  }
}
.content {
  padding: 3rem 0rem;
  display: grid;
  grid-gap: 1.6rem;
  .aside-title {
    color: color(white);
  }
  .contacts-wrapper {
    display: grid;
    grid-gap: 1rem;
    .status-title {
      color: color(gray, shade1);
      font-size: 0.875rem;
    }
  }
  .contacts {
    display: grid;
    grid-gap: 0.7rem;
    .contact {
      border-radius: 27px;
      padding: 3px 0;
      padding-left: 3px;
    }
  }
}
</style>
