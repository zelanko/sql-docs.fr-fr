---
title: "Utilisation d’ADO avec des langages de script | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e3e63f9389016dcd7e198d7d09099f94299bd19
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="using-ado-with-scripting-languages"></a>Utilisation d’ADO avec des langages de script
Dans un environnement de script, ADO vous permet d’exposer des données par le biais de script côté serveur. Dans ce scénario, ADO, le fournisseur OLE DB sous-jacent qu’il utilise, et tous les autres composants nécessaires pour faire référence à un magasin de données installées sur un serveur exécutant Internet Information Services (IIS). À l’aide d’Active Server Pages (ASP), ADO est un composant référencé dans un script qui peut générer du code HTML, par exemple. Ce contenu peut être passé via le protocole HTTP pour un navigateur Web client. À l’aide de scripts, la page Web peut renvoyer des actions au script côté serveur, ce qui vous permet de mettre à jour, de traverser ou afficher des données spécifiques.  
  
 Avant d’utiliser un objet ActiveX dans une page Web, il est important de savoir si l’objet est sécurisé pour le script. Lorsqu’un objet est considéré comme sécurisé pour le script, cela signifie que le contrôle ne peut pas prendre toute action néfaste sur l’ordinateur de l’utilisateur et par conséquent, peut être exécuté sans demander l’approbation de l’utilisateur. Le tableau suivant répertorie les objets ADO et indique s’ils sont sécurisés pour les scripts.  
  
|Objet|Sécurisée pour le script ?|  
|------------|-------------------------|  
|Connexion ADO|Oui|  
|Commande ADO|Non|  
|Paramètre ADO|Non|  
|Jeu d’enregistrements ADO|Oui|  
|Enregistrement ADO|Oui|  
|Flux de données ADO|Oui|  
|Erreur ADO|Non|  
|Catalogue ADOX|Non|  
|Ensemble de cellules ADOX|Non|  
|DataControl des services Bureau à distance|Oui|  
|Espace de données de services Bureau à distance|Oui|  
|DataFactory des services Bureau à distance|Non|  
  
 Le tableau suivant répertorie les fournisseurs inclus avec Windows DAC/MDAC et indique s’ils sont sécurisés pour les scripts.  
  
|Fournisseur|Sécurisée pour le script ?|  
|--------------|-------------------------|  
|Graphique à base de formes|Oui|  
|Conserver|Oui|  
|Remote|Oui|  
|Fournisseur OLE DB pour SQL Server (SQLOLEDB)|Non|  
|Fournisseur OLE DB pour ODBC (MSDASQL)|Non|  
  
## <a name="odbc-data-sources"></a>Sources de données ODBC  
 Une différence notable entre du code ADO script et non le script est la Source de données ODBC si utilisé. Pour les applications sans script, vous pouvez créer un DSN utilisateur dans l’administrateur de Source de données ODBC. Pour les scripts qui sont exécutent sous IIS, vous devez créer une source de données système ; Sinon, vos scripts ne reconnaîtront pas la source de données que vous avez créé. Cela s’applique à toutes les applications de script ADO à l’aide du fournisseur Microsoft OLE DB pour ODBC via Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Fait référence à la bibliothèque ADO  
 Non applicable avec les langages de script.  
  
## <a name="handling-events"></a>La gestion des événements  
 Non applicable avec les langages de script.  
  
 Les rubriques suivantes contiennent des informations plus spécifiques sur l’utilisation d’ADO avec des langages de script :  
  
-   [Programmation ADO VBScript](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [Programmation ADO JScript](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [À l’aide d’ADO avec Microsoft Visual Basic](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Utilisation d’ADO avec Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
