---
title: Telegram删除全部归档对话
date: 2024-04-05 20:34:10
category: Telegram
---

打开 [网页版 Telegram](https://web.telegram.org/a)，打开已归档对话，F12 控制台运行下面的代码

```js
(function () {
  function findFirstMember() {
    return document.querySelector(".ArchivedChats .ListItem");
  }

  function rightClickMember(member) {
    try {
      const memberInfo = member.querySelector(".ListItem-button");
      memberInfo.dispatchEvent(
        new MouseEvent("contextmenu", {
          bubbles: true,
          cancelable: false,
          view: window,
          button: 2,
          buttons: 0,
          clientX: memberInfo.getBoundingClientRect().x,
          clientY: memberInfo.getBoundingClientRect().y,
        })
      );
    } catch (e) {}
  }

  function clickRemove(member) {
    try {
      const removeBtn = document.querySelector(".icon-delete").parentNode;
      removeBtn.dispatchEvent(
        new MouseEvent("click", {
          bubbles: true,
          cancelable: false,
          view: window,
          button: 2,
          buttons: 0,
          clientX: removeBtn.getBoundingClientRect().x,
          clientY: removeBtn.getBoundingClientRect().y,
        })
      );
    } catch (e) {}
  }

  function confirmRemove() {
    try {
      const removeBtn = document.querySelector(".confirm-dialog-button");
      removeBtn.dispatchEvent(
        new MouseEvent("click", {
          bubbles: true,
          cancelable: false,
          view: window,
          button: 2,
          buttons: 0,
          clientX: removeBtn.getBoundingClientRect().x,
          clientY: removeBtn.getBoundingClientRect().y,
        })
      );
    } catch (e) {}
  }

  function performRemove() {
    const member = findFirstMember();
    rightClickMember(member);
    setTimeout(() => {
      clickRemove(member);
      setTimeout(() => {
        confirmRemove();
        setTimeout(performRemove, 100);
      }, 100);
    }, 100);
  }

  performRemove();
})();
```
