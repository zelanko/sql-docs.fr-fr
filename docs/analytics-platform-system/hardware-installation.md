---
title: Installation matérielle
description: Cet article explique comment déplacer, décompresser et installer le matériel de votre appareil SQL Server PDW. Cet article est purement informatif et est destiné à vous aider à comprendre le processus. Votre appliance doit être décompressée, installée et vérifiée avant d’être retournée. La participation des clients est requise pour les éléments tels que l’accès au centre de données, l’alimentation électrique et les connexions Ethernet.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 60e27e2251cd2f613ca00266d76d4aaaf3b5c442
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401122"
---
# <a name="hardware-installation-for-analytics-platform-system-aps-appliance"></a>Installation matérielle pour l’appliance Analytics Platform System (APS)
Cet article explique comment déplacer, décompresser et installer le matériel de votre appareil SQL Server PDW. Cet article est purement informatif et est destiné à vous aider à comprendre le processus. Votre appliance doit être décompressée, installée et vérifiée avant d’être retournée. La participation des clients est requise pour les éléments tels que l’accès au centre de données, l’alimentation électrique et les connexions Ethernet.  
  
## <a name="BeforeMoving"></a>Avant de déplacer des composants à partir du Dock de chargement  
Effectuez les tâches suivantes avant de déplacer, décompresser ou monter en rack les composants de l’appliance.  
  
|Tâche|Description|  
|--------|---------------|  
|Vérifier que tous les composants sont arrivés|Utilisez la nomenclature pour vérifier que tous les composants sont arrivés et se trouvent dans leurs palettes sur le quai de réception pour votre centre de données.|  
|Vérifier que le centre de données répond à la configuration requise pour l’appliance|Commencez cette tâche en examinant les spécifications matérielles et les diagrammes de câblage fournis par votre IHV. Les étapes suivantes fournissent des détails sur l’espace de rack et les exigences de connectivité.|  
|Vérifier que le centre de données dispose de l’espace disponible dans le rack|Vérifiez que le centre de données dispose de suffisamment d’espace pour tous les racks de l’appliance.<br /><br />Vérifiez que l’espace disponible dans le rack est vide et prêt à recevoir les racks de l’appliance.|  
|Vérifier que le centre de données répond aux exigences de connectivité|Vérifiez que le centre de données répond aux exigences de câblage des diagrammes de câblage.<br /><br />Vérifiez qu’il y a de la place pour tous les câbles et les cordons d’alimentation une fois que les nœuds de l’appareil sont montés en rack.|  
|Vérifier que les étages entre la station d’accueil et les racks répondent aux exigences de poids|Vérifiez que tous les revêtements de sol entre les palettes et les racks peuvent prendre en charge le poids des nœuds de l’appareil, en particulier dans les centres de données avec des étages élevés.<br /><br />Pour plus d’informations sur le poids de chaque composant, contactez votre IHV.|  
|Sécuriser le rack de centre de données|Sécurisez le rack de centre de données en place à l’aide d’équipements supplémentaires selon les besoins de votre centre de données, tels que les bandes de tremblements de terres dans des zones géographiques sujettes à des tremblements de tremblement.|  
|Préparer l’assistance au transport des composants|Déterminez à l’avance l’assistance, l’équipement et les outils dont vous aurez besoin pour gérer chaque composant en toute sécurité et sans causer de dommages.|  
  
## <a name="Moving"></a>Déplacez les racks du quai de chargement vers le centre de données.  
Chaque palette contient tous les composants d’un rack d’appliances, y compris les nœuds, les câbles, les cordons, etc.  
  
Utilisez la liste de vérification suivante pour déplacer chaque rack d’appliance de la palette au quai de chargement vers son emplacement de rack dans le centre de données. Déplacez d’abord le rack de contrôle, puis déplacez les autres racks de données de l’appliance.  
  
> [!WARNING]  
> Si vous n’effectuez pas ces étapes exactement comme décrit, vous risquez de nuire aux dommages corporels, d’endommager votre appareil SQL Server PDW ou d’autres problèmes.  
>   
> N’essayez jamais de soulever ou de déplacer un nœud d’appareil ou un autre composant lourd sans assistance ou équipement approprié. Contactez votre IHV pour obtenir des informations sur le poids de chaque composant afin de pouvoir déterminer à l’avance l’assistance, l’équipement et les outils dont vous aurez besoin pour gérer chaque composant en toute sécurité et sans causer de dommages.  
  
|Tâche|Description|  
|--------|---------------|  
|Vérifier que la palette est de niveau|Avant de commencer à déplacer ou déballer la palette, assurez-vous qu’elle est au niveau du sol.|  
|Déboulonr un nœud de la palette|En commençant par le haut de la palette, déboulonz le nœud supérieur de la palette.|  
|Déplacer le nœud vers un poupée ou un chariot pouvant prendre en charge le poids|Utilisez des rampes et des techniques de levage/déplacement appropriées pour déplacer le nœud vers un poupée ou un chariot pouvant prendre en charge le poids.|  
|Transporter le nœud dans le centre de données|Utilisez des techniques de levage/déplacement appropriées pour déplacer le nœud dans le rack du centre de données.|  
|Sécuriser le nœud dans le rack de centre de données|Sécurisez le nœud sur place dans le rack du centre de données.|  
|Répétez ces étapes pour le nœud ou le composant suivant|Répétez ces étapes pour déplacer le nœud suivant ou un autre composant d’appliance dans le centre de données.|  
  
## <a name="AfterMoving"></a>Installer des composants supplémentaires  
Utilisez la liste de vérification suivante pour installer les composants supplémentaires.  
  
|Tâche|Description||  
|--------|---------------|-|  
|Déballer et monter en rack les commutateurs et les PDU du réseau|Utilisez les diagrammes de rack pour placer les commutateurs réseau et les PDU à l’emplacement approprié dans le rack.||  
|Connectez les câbles InfiniBand et Ethernet en fonction des étiquettes de câble.|Consultez le diagramme de câblage. Chaque câble a une étiquette à chaque extrémité qui spécifie l’emplacement où il doit être connecté.||  
|Connecter tous les câbles d’alimentation|Consultez le diagramme de câblage.||  
|Mettez l’alimentation sur les racks et les PDU.|Connectez l’alimentation aux racks et des racks aux PDU. **N’mettez pas hors tension les autres composants de l’appliance à l’heure actuelle.**||  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
