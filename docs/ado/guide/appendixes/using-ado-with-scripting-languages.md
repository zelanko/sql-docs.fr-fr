---
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
ms.openlocfilehash: 71057caed6d28a2923e1c3735e10d20fccc9217d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761567"
---
# <a name="using-ado-with-scripting-languages"></a>Utilisation d’ADO avec les langages de script
Dans un environnement de script, ADO vous permet d’exposer des données par le biais de scripts côté serveur. Dans ce scénario, ADO, le fournisseur de OLE DB sous-jacent qu’il utilise et tous les autres composants nécessaires pour référencer un magasin de données donné sont installés sur un serveur exécutant Internet Information Services (IIS). À l’aide des pages d’Active Server (ASP), ADO est un composant référencé dans un script qui peut générer du code HTML, par exemple. Ce contenu HTML peut être transmis via HTTP à un navigateur Web client. En utilisant des scripts, la page Web peut renvoyer des actions au script côté serveur, ce qui vous permet de mettre à jour, parcourir ou afficher des données spécifiques.  
  
 Avant d’utiliser un objet ActiveX dans une page Web, il est important de savoir si l’objet est sécurisé pour l’écriture de scripts. Lorsqu’un objet est considéré comme sécurisé pour l’écriture de scripts, cela signifie que le contrôle ne peut pas prendre d’action nuisible sur l’ordinateur de l’utilisateur et peut donc être exécuté sans demander l’approbation de l’utilisateur. Le tableau suivant répertorie les objets ADO et indique s’ils sont sûrs pour l’écriture de scripts.  
  
|Object|Sécurisé pour l’écriture de scripts ?|  
|------------|-------------------------|  
|Connexion ADO|Yes|  
|Commande ADO|No|  
|Paramètre ADO|No|  
|Recordset ADO|Yes|  
|Enregistrement ADO|Yes|  
|Flux ADO|Yes|  
|Erreur ADO|No|  
|Catalogue ADOX|No|  
|CellSet, CellSet|No|  
|DataControl RDS|Yes|  
|RDS DataSpace|Yes|  
|Objet RDS DataFactory|No|  
  
 Le tableau suivant répertorie les fournisseurs inclus avec Windows DAC/MDAC, et indique s’ils sont sûrs pour l’écriture de scripts.  
  
|Fournisseur|Sécurisé pour l’écriture de scripts ?|  
|--------------|-------------------------|  
|Forme|Yes|  
|Persist|Yes|  
|Remote|Yes|  
|Fournisseur OLE DB pour SQL Server (SQLOLEDB)|No|  
|Fournisseur OLE DB pour ODBC (MSDASQL)|No|  
  
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
