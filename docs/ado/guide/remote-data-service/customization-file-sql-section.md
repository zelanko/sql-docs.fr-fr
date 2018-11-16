---
title: Fichier de personnalisation, Section SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5efa6587ade3a15ce4b45b7247da1c3a896f69ee
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558526"
---
# <a name="customization-file-sql-section"></a>Fichier de personnalisation, section SQL
Le **sql** section peut contenir une nouvelle chaîne SQL qui remplace la chaîne de commande client. S’il n’existe aucune chaîne SQL dans la section, la section sera ignorée.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 La nouvelle chaîne SQL peut être *paramétrable*. Autrement dit, les paramètres dans le **sql** section chaîne SQL (désigné par le ' ?' caractère) peuvent être remplacés par les arguments correspondants dans un *identificateur* dans la chaîne de commande client (désigné par un délimitée par des virgules liste entre parenthèses). L’identificateur et une liste d’arguments se comportent comme un appel de fonction.  
  
 Par exemple, supposons que la chaîne de commande client est `"CustomerByID(4)"`, l’en-tête de section SQL `[SQL CustomerByID]`, et la nouvelle chaîne de la section SQL est `"SELECT * FROM Customers WHERE CustomerID = ?".` génère le gestionnaire `"SELECT * FROM Customers WHERE CustomerID = 4"` et utiliser cette chaîne pour interroger la source de données.  
  
 Si la nouvelle instruction SQL est une chaîne vide (" »), alors la section est ignorée.  
  
 Si la nouvelle chaîne d’instruction SQL n’est pas valide, l’exécution de l’instruction échoue. Le paramètre client est ignoré. Vous pouvez effectuer cela intentionnellement pour « désactiver » toutes les commandes SQL de client en spécifiant :  
  
```console
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Syntaxe  
 Un chaîne d’entrée SQL de remplacement est au format :  
  
 **SQL=**   
 ***sqlString***  
  
|Élément|Description|  
|----------|-----------------|  
|**SQL**|Une chaîne littérale qui indique qu’il est une entrée de section SQL.|  
|***sqlString***|Une chaîne SQL qui remplace la chaîne du client.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section Connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Fichier de personnalisation, Section de journaux](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Fichier de personnalisation, Section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


