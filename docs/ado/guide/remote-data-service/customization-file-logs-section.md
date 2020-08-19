---
description: Fichier de personnalisation, section Logs
title: Section journaux des fichiers de personnalisation | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: rothja
ms.author: jroth
ms.openlocfilehash: 365b57f174f289317a7e8b3e09fe0c29b051ef64
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452251"
---
# <a name="customization-file-logs-section"></a>Fichier de personnalisation, section Logs
La section **logs** contient une entrée de fichier journal qui spécifie le nom d’un fichier qui enregistre les erreurs lors de l’opération du **DataFactory**.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 Une entrée de fichier journal se présente sous la forme suivante :  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Notes  
  
|Élément|Description|  
|----------|-----------------|  
|**Raise**|Chaîne littérale qui indique qu’il s’agit d’une entrée de fichier journal.|  
|*FileName*|Un chemin d’accès complet et un nom de fichier. Le nom de fichier par défaut est **c:\msdfmap.log**.|  
  
 Le fichier journal contient le nom d’utilisateur, HRESULT, la date et l’heure de chaque erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Section de connexion au fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Section SQL du fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Section UserList du fichier de personnalisation](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Fonctionnement du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


