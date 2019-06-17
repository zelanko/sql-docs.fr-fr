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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d41d5a0239f11882c135c27fd4af8e817e83b799
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702766"
---
# <a name="using-ado-with-scripting-languages"></a>Utilisation d’ADO avec les langages de script
Dans un environnement de script, ADO vous permet d’exposer les données par le biais de scripts côté serveur. Dans ce scénario, ADO, le fournisseur OLE DB sous-jacent qui il utilise, et tous les composants nécessaires pour faire référence à un magasin de données donné sont installés sur un serveur exécutant Internet Information Services (IIS). À l’aide de Active Server Pages (ASP), ADO est un composant référencé dans un script qui peut générer du code HTML, par exemple. Ce contenu HTML peut être passé via HTTP à un navigateur Web client. À l’aide de scripts, la page Web peut renvoyer des actions au script côté serveur, ce qui vous permet de mettre à jour, de traverser ou afficher des données spécifiques.  
  
 Avant d’utiliser un objet ActiveX dans une page Web, il est important de savoir si l’objet est sécurisé pour le script. Lorsqu’un objet est considéré comme sécurisé pour le script, cela signifie que le contrôle ne peut pas intervenir dangereux sur l’ordinateur de l’utilisateur et par conséquent, peut être exécuté sans demander l’approbation de l’utilisateur. Le tableau suivant répertorie les objets ADO et indique s’ils sont sécurisés pour les scripts.  
  
|Object|Sécurisée pour le script ?|  
|------------|-------------------------|  
|Connexion ADO|Oui|  
|Commande ADO|Non|  
|Paramètre ADO|Non|  
|Jeu d’enregistrements ADO|Oui|  
|Objet Record ADO|Oui|  
|ADO Stream|Oui|  
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
 Une différence notable entre du code ADO script et le script est la Source de données ODBC si utilisé. Pour les applications sans script, vous pouvez créer un DSN utilisateur dans l’administrateur de sources de données ODBC. Pour les scripts qui sont exécutent sous IIS, vous devez créer une source de données système ; sinon vos scripts ne reconnaîtront pas la source de données que vous avez créé. Cela s’applique à n’importe quelle application de script de ADO à l’aide du fournisseur Microsoft OLE DB pour ODBC via Microsoft IIS.  
  
## <a name="referencing-the-ado-library"></a>Fait référence à la bibliothèque ADO  
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
