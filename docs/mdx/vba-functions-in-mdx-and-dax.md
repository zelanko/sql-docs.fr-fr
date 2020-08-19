---
description: Fonctions VBA dans MDX et DAX
title: Fonctions VBA dans MDX et DAX | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 10658daae1321ac7e22af337ef946f5cfb6004cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429701"
---
# <a name="vba-functions-in-mdx-and-dax"></a>Fonctions VBA dans MDX et DAX


  Ce document contient une référence croisée de toutes les fonctions VBA disponibles dans [Visual Basic pour applications fonctions](https://msdn.microsoft.com/vba/language-reference-vba/articles/functions-visual-basic-for-applications) prises en charge dans MDX. en outre, la liste inclut une note lorsqu’il existe une équivalence fonctionnelle avec le langage DAX.  
  
## <a name="visual-basic-for-applications-functions-reference"></a>Référence des fonctions Visual Basic for Applications (VBA)  
  
|Nom de fonction|Prise en charge|Notes|  
|-------------------|---------------|-----------|  
|Abs|DAX, MDX||  
|Array|Non pris en charge||  
|Asc|MDX uniquement||  
|AscW|MDX uniquement||  
|Atn|MDX uniquement||  
|CallByName|Non pris en charge||  
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
|CLngLng|Non pris en charge||  
|CLngPtr|Non pris en charge||  
|Commande|Non pris en charge||  
|Cos|MDX uniquement||  
|CreateObject|Non pris en charge||  
|CSmpl|MDX uniquement||  
|CChaîne|MDX uniquement||  
|RéperCour|Non pris en charge||  
|CVar|MDX uniquement||  
|CVErr|Non pris en charge||  
|Date|MDX uniquement|**Avertissement** DAX implémente une fonction différente avec le même nom ; la fonction DATE (année, mois, jour), utilisée pour générer une valeur de type date à partir des arguments donnés|  
|AjDate|MDX uniquement|**Avertissement** DAX implémente une fonction différente avec le même nom ; fonction DATEADD ( \<dates> , <number_of_intervals>, \<interval> ), utilisée pour déplacer les dates données d’un certain nombre d’intervalles donnés|  
|DiffDate|MDX uniquement||  
|PartDate|MDX uniquement||  
|SérieDate|MDX uniquement||  
|ValDate|DAX, MDX||  
|Jour|DAX, MDX||  
|DDB|MDX uniquement||  
|Réper|Non pris en charge||  
|DoEvents|Non pris en charge||  
|Environ|Non pris en charge||  
|EOF|Non pris en charge||  
|Error|Non pris en charge||  
|Exp|DAX, MDX||  
|FileAttr|Non pris en charge||  
|DateHeureFich|Non pris en charge||  
|LongFich|Non pris en charge||  
|Filtrer|Non pris en charge|**Avertissement** MDX implémente une fonction différente avec le même nom ; la fonction FILTER (Set_Expression, Logical_Expression) retourne le jeu qui résulte du filtrage d’un jeu spécifié selon une condition de recherche à partir des arguments donnés.<br /><br /> **Avertissement** DAX implémente une fonction différente avec le même nom ; la fonction FILTER ( \<table> , \<filter> ) retourne une table qui représente un sous-ensemble d’une autre table ou expression à partir des arguments donnés.|  
|Correction|MDX uniquement||  
|Format (Visual Basic for Applications)|DAX, MDX||  
|FormatCurrency|Non pris en charge||  
|FormatDateTime|Non pris en charge||  
|FormatNumber|Non pris en charge||  
|FormatPercent|Non pris en charge||  
|FreeFile|Non pris en charge||  
|VC|MDX uniquement||  
|LireTousParam|Non pris en charge||  
|LireAttr|Non pris en charge||  
|GetObject|Non pris en charge||  
|GetSetting|Non pris en charge||  
|Hex|MDX uniquement||  
|Heure|DAX, MDX||  
|Iif|MDX uniquement|**Avertissement** DAX implémente une fonction similaire avec la fonction Name : IF (logical_test, value_if_true, value_if_false).|  
|IMEStatus|Non pris en charge||  
|Entrée|Non pris en charge||  
|InputBox|Non pris en charge||  
|InStr|MDX uniquement||  
|InStrRev|Non pris en charge||  
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
|IsObject|Non pris en charge||  
|Join|Non pris en charge||  
|LBound|Non pris en charge||  
|Minuscule|MDX uniquement||  
|Gauche|DAX, MDX||  
|NbCar|DAX, MDX||  
|Loc|Non pris en charge||  
|LOF|Non pris en charge||  
|Journal|MDX uniquement|**Important** DAX implémente une fonction différente avec le même nom ; fonction LOG (Number, base). Retourne le logarithme d'un nombre à la base spécifiée à partir des arguments fournis.|  
|SupprGauche|MDX uniquement||  
|MacID|Non pris en charge||  
|MacScript|Non pris en charge||  
|ExtracChaîne|DAX, MDX||  
|Minute|DAX, MDX||  
|MIRR|MDX uniquement||  
|Month|DAX, MDX||  
|MonthName|Non pris en charge||  
|MsgBox|Non pris en charge||  
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
|Replace|Non pris en charge||  
|RGB|MDX uniquement||  
|Right|DAX, MDX||  
|Aléat|MDX uniquement||  
|Round|DAX, MDX||  
|SupprDroite|MDX uniquement||  
|Seconde|DAX, MDX||  
|Seek|Non pris en charge||  
|Sgn|DAX, MDX||  
|Shell|Non pris en charge||  
|Sin|MDX uniquement||  
|AmorLin|MDX uniquement||  
|Espace|MDX uniquement||  
|Spc|Non pris en charge||  
|Split|Non pris en charge||  
|Racine|MDX uniquement||  
|NumChaîne|MDX uniquement||  
|CompChaîne|MDX uniquement||  
|ConvChaîne|MDX uniquement||  
|String|MDX uniquement||  
|StrReverse|Non pris en charge||  
|Commutateur|MDX uniquement||  
|SYD|MDX uniquement||  
|Onglet|Non pris en charge||  
|Tan|MDX uniquement||  
|Temps|Non pris en charge||  
|Minuteur|MDX uniquement||  
|SérieHeure|MDX uniquement||  
|VHeure|DAX, MDX||  
|SupprEspace|DAX, MDX||  
|TypeName|MDX uniquement||  
|UBound|Non pris en charge||  
|UCase|MDX uniquement||  
|Val|MDX uniquement||  
|VarType|Non pris en charge||  
|Jour de la semaine|DAX, MDX||  
|WeekdayName|Non pris en charge||  
|Year|DAX, MDX||  
  
  
