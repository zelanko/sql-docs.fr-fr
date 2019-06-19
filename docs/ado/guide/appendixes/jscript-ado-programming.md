---
title: Programmation ADO JScript | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5e53f1d6e30497282cce8e895f458d81660240d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701292"
---
# <a name="jscript-ado-programming"></a>Programmation ADO JScript
## <a name="creating-an-ado-project"></a>Création d’un projet ADO  
 Microsoft JScript ne prend pas en charge les bibliothèques de types, vous n’avez pas besoin de la référence ADO dans votre projet. Par conséquent, aucune fonctionnalité associée comme la saisie semi-automatique de ligne de commande n’est pris en charge. En outre, par défaut, les constantes énumérées ADO ne sont pas définis dans JScript.  
  
 Toutefois, ADO comporte deux fichiers contenant les définitions suivantes à utiliser avec JScript :  
  
-   Pour l’utilisation de script côté serveur Adojavas.inc, qui est installé dans les dossiers de la bibliothèque ADO.  
  
-   Pour l’utilisation de script côté client Adcjavas.inc, qui est installé dans les dossiers de la bibliothèque ADO.  
  
 Vous pouvez copier et coller des définitions de constantes à partir de ces fichiers dans vos pages ASP ou, si vous effectuez un script côté serveur, copiez le fichier Adojavas.inc dans un dossier sur votre site Web et y fait référence à partir de votre page ASP comme suit :  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Création d’objets ADO dans JScript  
 Vous devez plutôt utiliser la **CreateObject** appel de fonction :  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>Exemple JScript  
 Le code suivant est un exemple générique de programmation côté serveur en JScript dans un fichier de Active Server Page (ASP) qui ouvre un **Recordset** objet :  
  
```javascript
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
