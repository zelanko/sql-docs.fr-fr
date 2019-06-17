---
title: Obtenir des informations du fabricant de matériel - Analytique Platform System | Microsoft Docs
description: Informations à obtenir à partir de votre fabricant de matériel sur l’appliance Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 57b61ed7741bc6d36b7531a62416893e7cc10fb7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150231"
---
# <a name="information-to-obtain-from-your-ihv"></a>Informations à obtenir à partir de votre fabricant de matériel
Votre fournisseur de matériel indépendants (IHV) fournit la nouvelle appliance SQL Server PDW pour vous, ils offrent également des informations sur le matériel et la configuration qu’ils ont effectuées sur votre appliance. Vous devez ces informations pour administrer votre appliance.  
  
La liste suivante montre les informations qui ne sont généralement nécessaire de votre fabricant de matériel. Dans certains cas, des informations supplémentaires ou d’autres sont nécessaire. Vérifiez auprès de votre fabricant de matériel pour vous assurer que toutes les informations pertinentes a été transférées avec succès à la livraison de l’appliance.  
  
|||  
|-|-|  
|**Plus d’informations ou de Document**|**Description**|  
|Nomenclature (BOM)|Votre nomenclature répertorie les composants qui sont inclus dans votre appliance. Ces informations sont nécessaires pour confirmer que tous les composants ont été remis.<br /><br />**Important :** Votre nomenclature doit inclure des pondérations pour chacun des nœuds d’appliance et pour chaque rack complet. Ces informations sont importantes lorsque vous planifiez comment gérer et déplacer les composants de l’appliance, et pour vous assurer que votre centre de données peut prendre en charge l’appliance. Si votre marque BOM n’inclut pas les pondérations des nœuds, veillez à obtenir ces informations à partir de votre fabricant de matériel pour tous les nœuds.|  
|Schémas de câblage|Diagrammes de câblage montrent comment se connecter au réseau, câbles d’alimentation et autres pour chaque appliance rack. Ces diagrammes sont nécessaires lors de l’installation de l’appliance dans votre centre de données, et chaque fois que vous devez supprimer ou remplacer un composant.|  
|Besoins d’un rack|Avant votre appliance peut être installé dans votre centre de données, vous devez savoir si votre centre de données répond à la ventilation et la configuration requise de longueur de câble pour l’appliance, ainsi que la taille et la puissance requise pour les composants. Voir aussi nomenclature (nomenclature) ci-dessus pour plus d’informations sur les poids des composants matériel, qui est également requis.|  
  
