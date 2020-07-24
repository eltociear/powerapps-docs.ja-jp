---
title: ポータルのカスタム JavaScript を使用 | MicrosoftDocs
description: ポータルのフォームへカスタム JavaScript を追加する指示
author: sandhangitmsft
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: sandhan
ms.reviewer: tapanm
ms.openlocfilehash: fe9b1381149346a76d67da202a415f5d79e929d0
ms.sourcegitcommit: c12260f372ad2cc48d3146be570d2088c9ef1d86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2020
ms.locfileid: "3492172"
---
# <a name="add-custom-javascript"></a>カスタム JavaScript を追加する

Web フォーム ステップ レコードには、フォームの表示や機能を拡張または変更できる JavaScript コードの保存に使用できる **カスタム JavaScript** という名前のフィールドが含まれています。

JavaScript のカスタム ブロックは、ページの下部のクローズ フォーム タグ要素の直前に追加されます。

## <a name="form-fields"></a>フォーム フィールド

エンティティ フィールドの HTML インプット ID が、属性の論理名に設置されています。 これにより、フィールドの選択や値または他のクライアント側の操作の設置を [jQuery](https://jquery.com/) で簡単にします。  

```JavaScript
$(document).ready(function() {
   $("#address1_stateorprovince").val("Saskatchewan");
});
```

## <a name="additional-client-side-field-validation"></a>追加したクライアント側フィールドの検証
フォーム上で、フィールドの検証を時々カスタマイズする必要があります。 次の例は、カスタム 検証の追加を示します。 この例では、希望の連絡方法の為の他フィールドが電子メールに設置される場合のみ、ユーザーに電子メールを指定させます。

> [!NOTE]
> クライアント側のフィールド検証はサブグリッドではサポートされません。

```JavaScript
if (window.jQuery) {
   (function ($) {
      $(document).ready(function () {
         if (typeof (Page_Validators) == 'undefined') return;
         // Create new validator
         var newValidator = document.createElement('span');
         newValidator.style.display = "none";
         newValidator.id = "emailaddress1Validator";
         newValidator.controltovalidate = "emailaddress1";
         newValidator.errormessage = "<a href='#emailaddress1_label'>Email is a required field.</a>";
         newValidator.validationGroup = ""; // Set this if you have set ValidationGroup on the form
         newValidator.initialvalue = "";
         newValidator.evaluationfunction = function () {
            var contactMethod = $("#preferredcontactmethodcode").val();
            if (contactMethod != 2) return true; // check if contact method is not 'Email'.
            // only require email address if preferred contact method is email.
            var value = $("#emailaddress1").val();
            if (value == null || value == "") {
            return false;
            } else {
               return true;
            }
         };
 
         // Add the new validator to the page validators array:
         Page_Validators.push(newValidator);
 
         // Wire-up the click event handler of the validation summary link
         $("a[href='#emailaddress1_label']").on("click", function () { scrollToAndFocus('emailaddress1_label','emailaddress1'); });
      });
   }(window.jQuery));
}
```

## <a name="general-validation"></a>全般の検証

**次**/**送信**のボタンを押すと、**webFormClientValidate** という機能が実行されます。 この方法を拡張して、カスタム検証のロジックを追加できます。

```JavaScript
if (window.jQuery) {
   (function ($) {
      if (typeof (webFormClientValidate) != 'undefined') {
         var originalValidationFunction = webFormClientValidate;
         if (originalValidationFunction && typeof (originalValidationFunction) == "function") {
            webFormClientValidate = function() {
               originalValidationFunction.apply(this, arguments);
               // do your custom validation here
               // return false; // to prevent the form submit you need to return false
               // end custom validation.
               return true;
            };
         }
      }
   }(window.jQuery));
}
```
### <a name="see-also"></a>関連項目

[ポータルの構成](configure-portal.md)  
[エンティティ フォームの定義](entity-forms.md)  
[ポータルの Web フォームの手順](web-form-steps.md)  
[フォームの読み込みまたはタブの読み込みのステップの種類](load-form-step.md)  
[リダイレクト ステップの種類](add-redirect-step.md)  
[条件付きのステップの種類](add-conditional-step.md)
