---
title: Gestionnaire de connexions du cache | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c0d3513446c930d41ef9163708e60ad063244479
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064279"
---
# <a name="cache-connection-manager"></a>Gestionnaire de connexions du cache
  Le gestionnaire de connexions du cache lit des données à partir de la transformation du cache ou d'un fichier cache (.caw) et peut enregistrer les données dans un fichier cache. Les données sont toujours stockées en mémoire que vous configuriez ou non le gestionnaire de connexions du cache pour utiliser un fichier cache.  
  
 La transformation du cache écrit des données provenant d'une source de données connectée dans le flux de données dans un gestionnaire de connexions du cache. La transformation de recherche dans un package effectue des recherches sur les données.  
  
> [!NOTE]  
>  Le gestionnaire de connexions du cache ne prend pas en charge les types de données de l'objet BLOB (Binary Large Object) DT_TEXT, DT_NTEXT et DT_IMAGE. Si le dataset de référence contient un type de données d'objet BLOB, le composant échoue lorsque vous exécutez le package. Vous pouvez utiliser l' **Éditeur du gestionnaire de connexions du cache** pour modifier des types de données de colonne. Pour plus d’informations, consultez [Éditeur du gestionnaire de connexions du cache](../cache-connection-manager-editor.md).  
  
> [!NOTE]  
>  Le niveau de protection du package ne s'applique pas au fichier cache. Si le fichier cache contient des informations sensibles, utilisez une liste de contrôle d'accès (ACL) pour restreindre l'accès à l'emplacement ou au dossier dans lequel vous stockez le fichier. Vous devez autoriser l'accès à certains comptes uniquement. Pour plus d’informations, consultez [Accéder aux fichiers utilisés par des packages](../access-to-files-used-by-packages.md).  
  
## <a name="configuration-of-the-cache-connection-manager"></a>Configuration du gestionnaire de connexions du cache  
 Vous pouvez configurer le gestionnaire de connexions du cache comme suit :  
  
-   Indiquez s'il faut utiliser ou non un fichier cache.  
  
     Si vous configurez le gestionnaire de connexions du cache pour utiliser un fichier cache, il effectuera l'une des actions suivantes :  
  
    -   Il enregistrera les données dans le fichier lorsqu'une transformation du cache est configurée pour écrire des données depuis une source de données dans le flux de données dans le gestionnaire de connexions du cache.  
  
    -   Il lira des données à partir du fichier cache.  
  
     Pour plus d'informations, consultez [Cache Transform](../data-flow/transformations/cache-transform.md).  
  
-   Modifiez les métadonnées des colonnes stockées dans le cache.  
  
-   Mettez à jour le nom du fichier cache au moment de l’exécution en utilisant une expression pour définir la propriété ConnectionString. Pour plus d’informations, consultez [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md).  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , consultez [Éditeur du gestionnaire de connexions du cache](../cache-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programmation](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 [Implémenter une transformation de recherche en mode Cache complet à l'aide du gestionnaire de connexions du cache](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
