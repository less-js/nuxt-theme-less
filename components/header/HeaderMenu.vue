<script lang="ts" setup></script>

<template>
  <nav>
    <ul class="menu">
      <li class="menu-item">
        <NuxtLink class="menu-item-link" to="/">
          <span class="menu-item-text">Home</span>
          <i class="icon-arrow-down"></i>
        </NuxtLink>
        <div class="menu-dropdown">
          <HeaderMenuDropdown />
        </div>
      </li>
      <li class="menu-item">
        <NuxtLink class="menu-item-link" to="/">
          <span class="menu-item-text">Pages</span>
        </NuxtLink>
      </li>
      <li class="menu-item">
        <NuxtLink class="menu-item-link" to="/">
          <span class="menu-item-text">Portfolio</span>
        </NuxtLink>
      </li>
      <li class="menu-item">
        <NuxtLink class="menu-item-link" to="/">
          <span class="menu-item-text">Blog</span>
        </NuxtLink>
      </li>
      <li class="menu-item">
        <NuxtLink class="menu-item-link" to="/">
          <span class="menu-item-text">Elements</span>
        </NuxtLink>
      </li>
    </ul>
  </nav>
</template>

<style scoped lang="scss">
nav {
  display: flex;
  flex-grow: 1;
  justify-content: flex-end;

  .menu {
    display: flex;

    .menu-item {
      a {
        color: var(--nt-c-white-soft);
        font-weight: 600;
        line-height: 1.18;
        font-size: 16px;

        &.menu-item-link {
          margin-left: 13px;
          padding: 50px 5px;
          overflow: hidden;
          z-index: 1;
          transition: all 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);

          .menu-item-text {
            position: relative;
            margin: 0 10px;
            transition: all 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);

            &::after {
              content: '';
              width: 0;
              height: 1px;
              position: absolute;
              bottom: 0;
              left: auto;
              right: 0;
              z-index: -1;
              background: currentColor;
              transition: width 0.6s cubic-bezier(0.25, 0.8, 0.25, 1) 0s;
            }
          }

          .icon-arrow-down {
            &::after {
              position: relative;
              top: -2px;
              content: '';
              display: inline-block;
              width: 6px;
              height: 6px;
              margin-top: -2px;
              border-right: 2px solid var(--nt-c-white-soft);
              border-top: 2px solid var(--nt-c-white-soft);
              transform: rotate(135deg);
            }
          }
        }
      }

      &:hover {
        .menu-item-link {
          .menu-item-text {
            &::after {
              z-index: 1;
              width: 100%;
              left: 0;
              right: auto;
            }
          }
        }
        .menu-dropdown {
          opacity: 1;
          visibility: visible;
          animation: show-animation 0.3s;
        }
      }

      .menu-dropdown {
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        width: auto;
        min-width: 10em;
        max-width: none;
        margin-top: 0;
        margin-left: 0;
        padding: 70px 100px;
        box-shadow: 0 10px 37px rgb(0 0 0 / 7%);
        background-color: #222;
        opacity: 0;
        visibility: hidden;
        animation: hide-animation 0.3s;
      }

      @keyframes hide-animation {
        0% {
          opacity: 1;
          transform: translateY(0);
        }
        to {
          opacity: 0;
          transform: translateY(50px);
        }
      }

      @keyframes show-animation {
        0% {
          opacity: 0;
          transform: translateY(50px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }
    }
  }
}
</style>
