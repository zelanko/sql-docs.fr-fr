---
description: Utilisation d’ADO avec les langages de script
title: Utilisation d’ADO avec les langages de script | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
author: rothja
ms.author: jroth
ms.openlocfilehash: 6decee7fddc4748a7d0931ab671f66b11161cc9c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453991"
---
# <a name="using-ado-with-scripting-languages"></a>Utilisation d’ADO avec les langages de script
Dans un environnement de script, ADO vous permet d’exposer des données par le biais de scripts côté serveur. Dans ce scénario, ADO, le fournisseur de OLE DB sous-jacent qu’il utilise et tous les autres composants nécessaires pour référencer un magasin de données donné sont installés sur un serveur exécutant Internet Information Services (IIS). À l’aide des pages d’Active Server (ASP), ADO est un composant référencé dans un script qui peut générer du code HTML, par exemple. Ce contenu HTML peut être transmis via HTTP à un navigateur Web client. En utilisant des scripts, la page Web peut renvoyer des actions au script côté serveur, ce qui vous permet de mettre à jour, parcourir ou afficher des données spécifiques.  
  
 Avant d’utiliser un objet ActiveX dans une page Web, il est important de savoir si l’objet est sécurisé pour l’écriture de scripts. Lorsqu’un objet est considéré comme sécurisé pour l’écriture de scripts, cela signifie que le contrôle ne peut pas prendre d’action nuisible sur l’ordinateur de l’utilisateur et peut donc être exécuté sans demander l’approbation de l’utilisateur. Le tableau suivant répertorie les objets ADO et indique s’ils sont sûrs pour l’écriture de scripts.  
  
|Object|Sécurisé pour l’écriture de scripts ?|  
|------------|-------------------------|  
|Connexion ADO|Oui|  
|Commande ADO|Non|  
|Paramètre ADO|Non|  
|Recordset ADO|Oui|  
|Enregistrement ADO|Oui|  
|Flux ADO|Oui|  
|Erreur ADO|Non|  
|Catalogue ADOX|Non|  
|CellSet, CellSet|Non|  
|DataControl RDS|Oui|  
|RDS DataSpace|Oui|  
|Objet RDS DataFactory|Non|  
  
 Le tableau suivant répertorie les fournisseurs inclus avec Windows DAC/MDAC, et indique s’ils sont sûrs pour l’écriture de scripts.  
  
|Fournisseur|Sécurisé pour l’écriture de scripts ?|  
|--------------|-------------------------|  
|Forme|Oui|  
|Conserver|Oui|  
|Remote|Oui|  
|Fournisseur OLE DB pour SQL Server (SQLOLEDB)|Non|  
|Fournisseur OLE DB pour ODBC (MSDASQL)|Non|  
  
## <a name="odbc-data-sources"></a>Sources de données ODBC  
 L’une des différences notables entre le script et le non-script ADO est la source de données ODBC, si elle est utilisée. Pour les applications sans script, vous pouvez créer un DSN utilisateur dans l’administrateur de la source de données ODBC. Pour les scripts qui s’exécutent sous IIS, vous devez créer un DSN système. dans le cas contraire, vos scripts ne reconnaîtront pas la source de données que vous avez créée. Cela s’applique à toute application de script ADO qui utilise le fournisseur Microsoft OLE DB pour ODBC par le biais de Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Référencement de la bibliothèque ADO  
 Non applicable avec les langages de script.  
  
## <a name="handling-events"></a>Gestion des événements  
 Non applicable avec les langages de script.  
  
 Les rubriques suivantes contiennent des informations plus spécifiques sur l’utilisation d’ADO avec les langages de script :  
  
-   [Programmation ADO VBScript](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [Programmation ADO JScript](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Utilisation d’ADO avec Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Utilisation d’ADO avec Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
