---
title: Installation matérielle - Analytique Platform System | Microsoft Docs
description: Cet article décrit comment déplacer, décompresser et installer le matériel de votre appliance SQL Server PDW. Cet article est d’information uniquement et est destiné à vous aider à comprendre le processus. Votre appliance doit être décompressé, installé et vérifié avant qu’il soit retourné à vous. La participation du client est requise pour les éléments tels que les données du centre accès, alimentation électrique et connexions Ethernet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 169b38a1228f909a79d7866eba20b85b4a56c30b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157318"
---
# <a name="hardware-installation-for-analytics-platform-system-appliance"></a>Installation matérielle pour l’appliance d’Analytique Platform System
Cet article décrit comment déplacer, décompresser et installer le matériel de votre appliance SQL Server PDW. Cet article est d’information uniquement et est destiné à vous aider à comprendre le processus. Votre appliance doit être décompressé, installé et vérifié avant qu’il soit retourné à vous. La participation du client est requise pour les éléments tels que les données du centre accès, alimentation électrique et connexions Ethernet.  
  
## <a name="BeforeMoving"></a>Avant de déplacer tous les composants du quai de chargement  
Effectuer les tâches suivantes avant de vous déplacez, décompressez ou monter en rack de tous les composants de l’appliance.  
  
|Tâche|Description|  
|--------|---------------|  
|Vérifiez que tous les composants sont arrivés.|Utilisez la nomenclature (nomenclature) pour vérifier que tous les composants sont arrivés et sont leurs palettes à l’écran d’ancrage réception pour votre centre de données.|  
|Vérifiez que le centre de données répond à toutes les conditions requises pour l’appliance|Cette tâche de démarrage en examinant les spécifications matérielles et en fournissant par votre fabricant de matériel des schémas de câblage. Les étapes suivantes fournissent plus de détails sur le rack les exigences de connectivité et d’espace.|  
|Vérifiez que le centre de données dispose d’espace en rack approprié|Vérifiez que le centre de données dispose de suffisamment d’espace pour tous les racks de l’appliance.<br /><br />Vérifiez que l’espace d’armoire est vide et prêt à recevoir les racks de l’appliance.|  
|Vérifiez que le centre de données répond aux exigences de connectivité|Vérifiez que le centre de données remplit les conditions de câblage dans les diagrammes de câblage.<br /><br />Vérifiez qu’il n’y place pour tous les câbles et les câbles d’alimentation une fois que les nœuds d’appliance sont montés en rack.|  
|Vérifiez que les étages entre la station d’accueil et les racks répondent aux exigences de poids|Vérifiez que tous les revêtement de sol entre les palettes et les racks peut prendre en charge le poids des nœuds d’appliance, en particulier dans les centres de données avec des étages déclenchés.<br /><br />Contactez votre fabricant de matériel pour plus d’informations sur le poids de chaque composant.|  
|Sécuriser le centre de données en rack|Sécuriser le centre de données rack en place à l’aide d’équipement supplémentaire en fonction des besoins de votre emplacement de centre de données, telles que des bandes pour un tremblement de terre dans des zones géographiques susceptibles d’engendrer des tremblements de terre.|  
|Préparer pour obtenir une assistance avec le transport les composants|Déterminer à l’avance le type d’assistance, les équipements et les outils que vous devrez gérer chaque composant et en toute sécurité sans provoquer des dommages.|  
  
## <a name="Moving"></a>Déplacer les Racks du quai de chargement dans le centre de données  
Chaque palette contient tous les composants pour rack une appliance, y compris les nœuds, câbles, câbles, etc.  
  
Utilisez la liste de vérification suivante pour déplacer chaque rack de l’appliance à partir de la palette au niveau de l’écran d’ancrage le chargement vers son emplacement de rack dans le centre de données. Déplacez d’abord le rack de contrôle, puis déplacer les autres racks de données d’appliance.  
  
> [!WARNING]  
> Pour effectuer ces étapes exactement comme décrit peut provoquer des dommages corporels, dommages subis par votre appliance SQL Server PDW, ou d’autres problèmes.  
>   
> Jamais tentative de courbes d’élévation ou déplacer un nœud de l’appliance ou un autre composant importante sans assistance ou d’équipement approprié. Contactez votre fabricant de matériel pour plus d’informations sur le poids de chaque composant afin que vous pouvez déterminer à l’avance le type d’assistance, les équipements et les outils que vous devrez gérer chaque composant et en toute sécurité sans provoquer des dommages.  
  
|Tâche|Description|  
|--------|---------------|  
|Vérifiez que la palette est de niveau|Avant de commencer à déplacer ou décompresser la palette, assurez-vous que sur le terrain.|  
|Dégager un nœud à partir de la palette|En commençant par le haut de la palette, dégager le nœud supérieur de la palette.|  
|Déplacer le nœud vers un chariot ou d’un panier prenant en charge le poids|Utiliser des chemins d’entrée et les techniques de soulever/déplacement des appropriée pour déplacer le nœud à un chariot ou d’un panier prenant en charge le poids.|  
|Le nœud de transport dans le centre de données|Utiliser des techniques de soulever/déplacement appropriés pour déplacer le nœud à la position dans le rack de centre de données.|  
|Sécuriser le nœud dans le centre de données en rack|Sécuriser le nœud en place dans le centre de données en rack.|  
|Répétez ces étapes pour le nœud ou le composant suivant|Répétez ces étapes pour déplacer le nœud suivant ou un autre composant de l’appliance dans le centre de données.|  
  
## <a name="AfterMoving"></a>Installer des composants supplémentaires  
Utilisez la liste de vérification suivante pour installer les composants supplémentaires.  
  
|Tâche|Description||  
|--------|---------------|-|  
|Décompresser et commutateurs réseau et les PDU en rack|Utilisez les diagrammes de rack pour placer les commutateurs de réseau et les PDU à l’emplacement approprié dans le rack.||  
|Connectez les câbles Infiniband et Ethernet selon les étiquettes de câble|Consultez le schéma de câblage. Chaque câble a une étiquette à chaque extrémité qui spécifie où il doit être connecté.||  
|Connecter tous les câbles d’alimentation|Consultez le schéma de câblage.||  
|Activer l’alimentation pour les racks et les PDU|Connectez l’alimentation aux racks et à partir des racks pour les PDU. **Ne pas en marche les autres composants de l’appliance pour l’instant.**||  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
