---
title: Fonctions VBA dans MDX et DAX | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 39a0db181f3b1d1a40af1a5fa27ba78366a9d2b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68135019"
---
# <a name="vba-functions-in-mdx-and-dax"></a>Fonctions VBA dans MDX et DAX


  Ce document contient une référence croisée de toutes les fonctions VBA disponibles dans [Visual Basic pour applications fonctions](https://msdn.microsoft.com/vba/language-reference-vba/articles/functions-visual-basic-for-applications) prises en charge dans MDX. en outre, la liste inclut une note lorsqu’il existe une équivalence fonctionnelle avec le langage DAX.  
  
## <a name="visual-basic-for-applications-functions-reference"></a>Référence des fonctions Visual Basic for Applications (VBA)  
  
|Nom de fonction|Pris en charge|Notes|  
|-------------------|---------------|-----------|  
|Abs|DAX, MDX||  
|Array|Non prise en charge||  
|Asc|MDX uniquement||  
|AscW|MDX uniquement||  
|Atn|MDX uniquement||  
|CallByName|Non prise en charge||  
|CBool|MDX uniquement||  
|CByte|MDX uniquement||  
|CMonnaie|MDX uniquement||  
|CDate|MDX uniquement||  
|CDbl|MDX uniquement||  
|CDec|MDX uniquement||  
|Choose|MDX uniquement||  
|Chr|MDX uniquement||  
|CEnt|MDX uniquement||  
|CLong|MDX uniquement||  
|CLngLng|Non prise en charge||  
|CLngPtr|Non prise en charge||  
|Commande|Non prise en charge||  
|Cos|MDX uniquement||  
|CreateObject|Non prise en charge||  
|CSmpl|MDX uniquement||  
|CChaîne|MDX uniquement||  
|RéperCour|Non prise en charge||  
|CVar|MDX uniquement||  
|CVErr|Non prise en charge||  
|Date|MDX uniquement|**Avertissement** DAX implémente une fonction différente avec le même nom ; la fonction DATE (année, mois, jour), utilisée pour générer une valeur de type date à partir des arguments donnés|  
|AjDate|MDX uniquement|**Avertissement** DAX implémente une fonction différente avec le même nom ; fonction DATEADD (\<dates>, <number_of_intervals>,\<Interval>), utilisée pour déplacer les dates données d’un certain nombre d’intervalles donnés|  
|DiffDate|MDX uniquement||  
|PartDate|MDX uniquement||  
|SérieDate|MDX uniquement||  
|ValDate|DAX, MDX||  
|jour|DAX, MDX||  
|DDB|MDX uniquement||  
|Réper|Non prise en charge||  
|DoEvents|Non prise en charge||  
|Environ|Non prise en charge||  
|EOF|Non prise en charge||  
|Error|Non prise en charge||  
|Exp|DAX, MDX||  
|FileAttr|Non prise en charge||  
|DateHeureFich|Non prise en charge||  
|LongFich|Non prise en charge||  
|Filtrer|Non prise en charge|**Avertissement** MDX implémente une fonction différente avec le même nom ; la fonction FILTER (Set_Expression, Logical_Expression) retourne le jeu qui résulte du filtrage d’un jeu spécifié selon une condition de recherche à partir des arguments donnés.<br /><br /> **Avertissement** DAX implémente une fonction différente avec le même nom ; la fonction FILTER\<(table>\<, filtre>) retourne une table qui représente un sous-ensemble d’une autre table ou expression à partir des arguments donnés.|  
|Fix|MDX uniquement||  
|Format (Visual Basic for Applications)|DAX, MDX||  
|FormatCurrency|Non prise en charge||  
|FormatDateTime|Non prise en charge||  
|FormatNumber|Non prise en charge||  
|FormatPercent|Non prise en charge||  
|FreeFile|Non prise en charge||  
|VC|MDX uniquement||  
|LireTousParam|Non prise en charge||  
|LireAttr|Non prise en charge||  
|GetObject|Non prise en charge||  
|GetSetting|Non prise en charge||  
|Hex|MDX uniquement||  
|Heure|DAX, MDX||  
|Iif|MDX uniquement|**Avertissement** DAX implémente une fonction similaire avec la fonction Name : IF (logical_test, value_if_true, value_if_false).|  
|IMEStatus|Non prise en charge||  
|Entrée|Non prise en charge||  
|InputBox|Non prise en charge||  
|InStr|MDX uniquement||  
|InStrRev|Non prise en charge||  
|Int|DAX, MDX||  
|IPmt|MDX uniquement||  
|IRR|MDX uniquement||  
|IsArray|MDX uniquement||  
|IsDateMDX uniquement||  
|IsEmpty|MDX uniquement||  
|IsError|DAX, MDX||  
|IsMissing|MDX uniquement||  
|IsNull|MDX uniquement||  
|IsNumeric|MDX uniquement||  
|IsObject|Non prise en charge||  
|Join|Non prise en charge||  
|LBound|Non prise en charge||  
|Minuscule|MDX uniquement||  
|Gauche|DAX, MDX||  
|NbCar|DAX, MDX||  
|Loc|Non prise en charge||  
|LOF|Non prise en charge||  
|Journal|MDX uniquement|**Important** DAX implémente une fonction différente avec le même nom ; fonction LOG (Number, base). Retourne le logarithme d'un nombre à la base spécifiée à partir des arguments fournis.|  
|SupprGauche|MDX uniquement||  
|MacID|Non prise en charge||  
|MacScript|Non prise en charge||  
|ExtracChaîne|DAX, MDX||  
|Minute|DAX, MDX||  
|MIRR|MDX uniquement||  
|Month|DAX, MDX||  
|MonthName|Non prise en charge||  
|MsgBox|Non prise en charge||  
|maintenant|DAX, MDX||  
|NPer|MDX uniquement||  
|NPV|MDX uniquement||  
|Oct|MDX uniquement||  
|Partition|MDX uniquement||  
|Vpm|MDX uniquement||  
|PPmt|MDX uniquement||  
|PV|MDX uniquement||  
|RVBC|MDX uniquement||  
|Tarif|MDX uniquement||  
|Replace|Non prise en charge||  
|RGB|MDX uniquement||  
|Right|DAX, MDX||  
|Aléat|MDX uniquement||  
|Round|DAX, MDX||  
|SupprDroite|MDX uniquement||  
|Seconde|DAX, MDX||  
|Seek|Non prise en charge||  
|Sgn|DAX, MDX||  
|Shell|Non prise en charge||  
|Sin|MDX uniquement||  
|AmorLin|MDX uniquement||  
|Espace|MDX uniquement||  
|Spc|Non prise en charge||  
|Split|Non prise en charge||  
|Racine|MDX uniquement||  
|NumChaîne|MDX uniquement||  
|CompChaîne|MDX uniquement||  
|ConvChaîne|MDX uniquement||  
|String|MDX uniquement||  
|StrReverse|Non prise en charge||  
|Commutateur|MDX uniquement||  
|SYD|MDX uniquement||  
|Onglet|Non prise en charge||  
|Tan|MDX uniquement||  
|Heure|Non prise en charge||  
|Minuterie|MDX uniquement||  
|SérieHeure|MDX uniquement||  
|VHeure|DAX, MDX||  
|SupprEspace|DAX, MDX||  
|TypeName|MDX uniquement||  
|UBound|Non prise en charge||  
|UCase|MDX uniquement||  
|Val|MDX uniquement||  
|VarType|Non prise en charge||  
|Jour de la semaine|DAX, MDX||  
|WeekdayName|Non prise en charge||  
|Year|DAX, MDX||  
  
  
