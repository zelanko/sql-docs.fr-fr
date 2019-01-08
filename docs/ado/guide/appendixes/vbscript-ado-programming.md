---
title: Programmation ADO VBScript | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a2b6172fdd35e98d1b4a5f1b3c6ff19293a7f81
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214680"
---
# <a name="vbscript-ado-programming"></a>Programmation ADO VBScript
## <a name="creating-an-ado-project"></a>Création d’un projet ADO  
 Microsoft Visual Basic, Scripting Edition ne prend pas en charge les bibliothèques de types, vous n’avez pas besoin de référencer ADO dans votre projet. Par conséquent, aucune fonctionnalité associée comme la saisie semi-automatique de ligne de commande n’est pris en charge. En outre, par défaut, les constantes énumérées ADO ne sont pas définis dans VBScript.  
  
 Toutefois, ADO comporte deux fichiers contenant les définitions suivantes à utiliser avec VBScript :  
  
-   Pour l’utilisation de script côté serveur Adovbs.inc, lequel est installé dans le dossier c:\Program Files\Common Files\System\ado\ par défaut.  
  
-   Pour l’utilisation de script côté client Adcvbs.inc, lequel est installé dans le dossier c:\Program Files\Common Files\System\msdac\ par défaut.  
  
 Vous pouvez copier et coller des définitions de constantes à partir de ces fichiers dans vos pages ASP ou, si vous effectuez un script côté serveur, copiez le fichier Adovbs.inc dans un dossier sur votre site Web et référencez-le dans votre page ASP comme suit :  
  
```vb
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Création d’objets ADO dans VBScript  
 Vous ne pouvez pas utiliser le **Dim** instruction pour assigner des objets à un type spécifique dans VBScript. En outre, VBScript ne prend pas en charge la **New** syntaxe utilisée avec le **Dim** instruction en Visual Basic pour Applications. Vous devez plutôt utiliser la **CreateObject** appel de fonction :  
  
```vb
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Exemples de VBScript  
 Le code suivant est un exemple générique de programmation côté serveur en VBScript dans un fichier de Active Server Page (ASP) :  
  
```vb
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Des exemples VBScript plus spécifiques sont inclus dans la documentation d’ADO. Pour plus d’informations, consultez [exemples de Code ADO dans Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Différences entre VBScript et Visual Basic  
 Utilisation d’ADO avec VBScript est similaire à l’aide d’ADO avec Visual Basic dans bien des égards, y compris la syntaxe est utilisée. Toutefois, il existe quelques différences importantes :  
  
-   VBScript prend en charge uniquement le type de données Variant, qui peut contenir différents types de données. Vous pouvez stocker les données que vous avez besoin dans un type de données Variant, et les données ne fonctionnera correctement en raison de casting effectué par VBScript. Il reconnaît le type requis par ADO et convertit la valeur de la variante en conséquence.  
  
-   Vous ne pouvez pas utiliser **sur erreur goto \<étiquette >** dans VBScript.  
  
-   VBScript prend en charge les certaines des fonctions Visual Basic intégrées telles que **Msgbox**, **Date**, et **IsNumeric**. Toutefois, étant donné que VBScript est un sous-ensemble de Visual Basic, pas toutes les fonctions intégrées sont prises en charge. Par exemple, VBScript ne prend pas en charge la **Format** fonction et aux fonctions d’e/s de fichier.
