---
title: Section SQL du fichier de personnalisation | Microsoft Docs
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
ms.openlocfilehash: 6163a5b5fd0999e17e17961639e0a1fee3e8fa4c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922797"
---
# <a name="customization-file-sql-section"></a>Fichier de personnalisation, section SQL
La section **SQL** peut contenir une nouvelle chaîne SQL qui remplace la chaîne de commande du client. S’il n’existe aucune chaîne SQL dans la section, la section sera ignorée.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 La nouvelle chaîne SQL peut être *paramétrable*. Autrement dit, les paramètres de la chaîne SQL de la section **SQL** (désignés par le caractère «  ? ») peuvent être remplacés par des arguments correspondants dans un *identificateur* dans la chaîne de commande cliente (désignée par une liste délimitée par des virgules entre parenthèses). L’identificateur et la liste d’arguments se comportent comme un appel de fonction.  
  
 Par exemple, supposons que la chaîne de `"CustomerByID(4)"`commande du client est, que `[SQL CustomerByID]`l’en-tête de la section SQL `"SELECT * FROM Customers WHERE CustomerID = ?".` soit et que la `"SELECT * FROM Customers WHERE CustomerID = 4"` nouvelle chaîne de la section SQL soit le gestionnaire génère et utilise cette chaîne pour interroger la source de données.  
  
 Si la nouvelle instruction SQL est la chaîne null (""), la section est ignorée.  
  
 Si la nouvelle chaîne d’instruction SQL n’est pas valide, l’exécution de l’instruction échoue. Le paramètre client est effectivement ignoré. Vous pouvez effectuer cette opération intentionnellement pour « désactiver » toutes les commandes SQL clientes en spécifiant :  
  
```console
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Syntaxe  
 Une entrée de chaîne SQL de remplacement se présente sous la forme suivante :  
  
 **SQL =**   
 ***sqlString***  
  
|Élément|Description|  
|----------|-----------------|  
|**Server**|Chaîne littérale qui indique qu’il s’agit d’une entrée de section SQL.|  
|***sqlString***|Chaîne SQL qui remplace la chaîne du client.|  
  
## <a name="see-also"></a>Voir aussi  
 [Section de connexion au fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Section journaux des fichiers de personnalisation](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Section UserList du fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Fonctionnement du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


