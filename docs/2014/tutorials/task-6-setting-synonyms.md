---
title: 'Aufgabe 6: Festlegen von Synonymen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a81a538e2cd15dd38a6c32993395cac20079b6f2
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022274"
---
# <a name="task-6-setting-synonyms"></a>Aufgabe 6: Festlegen von Synonymen
  In dieser Aufgabe legen Sie zwei Domänenwerte, **USA** und **USA**, der die **Land** Domäne als Synonyme mit **USA** wie die führender Wert. Da die **führende Werte** ausgewählt war beim Erstellen der **Land** Domäne alle **USA** Werte für die **Land** Domäne Gibt als **USA** (wie der Vereinigten Staaten der führende Wert ist). Finden Sie unter [Change Domain Values](https://msdn.microsoft.com/library/hh510408.aspx) Weitere Details.  
  
1.  Wählen Sie **Land** aus der Liste der Domänen.  
  
2.  Wechseln Sie zu der **Domänenwerte** Registerkarte.  
  
3.  Klicken Sie auf **neuen Domänenwert hinzufügen** auf der Symbolleiste.  
  
4.  Typ **USA** für den Wert und drücken Sie **EINGABETASTE**.  
  
5.  MultiSelect **USA** und **USA** STRG- oder UMSCHALTTASTE rechten Maustaste auf die ausgewählten Elemente, und klicken Sie dann auf **als Synonyme festlegen**. DQS gruppiert diese Werte und legt einen der Werte als führenden Wert fest, durch den die anderen Werte ersetzt werden.  
  
     ![Legen Sie als Synonyme Menü](../../2014/tutorials/media/et-settingsynonyms-01.jpg "als Synonyme Menü festlegen")  
  
6.  Beachten Sie, dass **USA** als führender Wert festgelegt ist. Wenn USA der führende Wert sein soll, können Sie mit der rechten Maustaste auf die USA und auswählen **als führend festlegen** Option. In diesem Tutorial verwenden wir **USA** als führenden Wert fest.  
  
     ![Vereinigte Staaten und USA als Synonyme](../../2014/tutorials/media/et-settingsynonyms-02.jpg "Vereinigte Staaten und USA als Synonyme")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 7: Erstellen einer Verbunddomäne](../../2014/tutorials/task-7-creating-a-composite-domain.md)  
  
  
