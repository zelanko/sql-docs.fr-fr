---
title: Boîte de dialogue Propriétés de Analysis Server (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9bcb19e10417c24b30b5ee6346d6d6a19d4bbcb
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145094"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a>Boîte de dialogue Propriétés de Analysis Server (Analysis Services)
  Utilisez la boîte de dialogue **Propriétés de Analysis Server** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les paramètres généraux, de langue/classement et de sécurité d’une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour afficher la boîte de dialogue **Propriétés de Analysis Server**, cliquez avec le bouton droit de la souris sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans **l’Explorateur d’objets**, puis sélectionnez **Propriétés** dans le menu contextuel. Cette boîte de dialogue **Propriétés de Analysis Server** contient les propriétés suivantes.  
  
## <a name="information-properties"></a>Propriétés d'informations  
 Utilisez cette page pour afficher le mode serveur, la version et le niveau de compatibilité. Chaque instance est installée en mode serveur multidimensionnel ou tabulaire, avec la possibilité de charger des modèles multidimensionnels ou tabulaires. Si vous devez prendre en charge les deux modes, vous devez installer deux instances.  
  
 **Niveau de compatibilité pris en charge** est équivalente à la `DefaultCompatibilityLevel` propriété dans AMO. En lecture seule, en fonction du mode de déploiement du serveur spécifié au cours de l'installation. Le serveur vérifie cette propriété lors de la réalisation d'opérations qui varient en fonction de la version ou du mode serveur, telles que la restauration d'une sauvegarde de base de données tabulaire sur une instance de serveur tabulaire. Ne confondez pas cette propriété avec le mode de compatibilité de base de données des modèles tabulaires ou multidimensionnels, qui présentent des noms et des valeurs similaires. Les valeurs valides pour cette propriété de serveur sont les suivantes :  
  
-   **1100** est le niveau de compatibilité par défaut pour un mode de déploiement de 0, pour le mode multidimensionnel ou d'exploration de données.  
  
-   **1103** est le niveau de compatibilité par défaut pour les modes de déploiement 1 ou 2, pour les installations prenant en charge le mode tabulaire ou [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)].  
  
 Le serveur retourne cette valeur lorsqu'un client prenant en charge l'espace de noms demande DISCOVER_XML_METADATA. Pour plus d’informations, consultez [Ensemble de lignes DISCOVER_XML_METADATA](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset).  
  
## <a name="general-properties"></a>Propriétés générales  
 Cette page permet de définir les propriétés générales simples et avancées, telles que les emplacements de dossiers et les paramètres de réseau, relatives à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 La page de propriétés du serveur affiche uniquement les propriétés qu'un administrateur est le plus susceptible de modifier, telles que les propriétés du pool de threads et de mémoire, utilisées pour régler le serveur dans certaines configurations. La liste suivante fournit des liens vers les principaux groupes de propriétés :  
  
-   [Propriétés générales](server-properties/general-properties.md)  
  
-   [Propriétés de l’exploration de données](server-properties/data-mining-properties.md)  
  
-   [Propriétés de fonctionnalité](server-properties/feature-properties.md)  
  
-   [Propriétés du cache de fichiers](server-properties/filestore-properties.md)  
  
-   [Propriétés du gestionnaire de verrous](server-properties/lock-manager-properties.md)  
  
-   [Propriétés du journal](server-properties/log-properties.md)  
  
-   [Propriétés de mémoire](server-properties/memory-properties.md)  
  
-   [Propriétés réseau](server-properties/network-properties.md)  
  
-   [Propriétés OLAP](server-properties/olap-properties.md)  
  
-   [Propriétés de sécurité](server-properties/security-properties.md)  
  
-   [Propriétés du pool de threads](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a>Propriétés de langue/classement  
 Cette page sert à définir les options de langue et de classement par défaut pour une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La liste suivante contient une brève description de chaque option. Pour des descriptions plus détaillées, consultez [Langues et classements &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md).  
  
-   **Binaire** permet de trier et de comparer les données en fonction des modèles binaires définis pour chaque caractère. L'ordre de tri binaire respecte la casse, c'est-à-dire que les minuscules précèdent les majuscules ; il respecte également les accents. Il s'agit de l'ordre de tri le plus rapide.  
  
     Si cette option n'est pas activée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] respecte les règles de tri et de comparaison définies dans les dictionnaires pour la langue ou l'alphabet associé.  
  
    > [!NOTE]  
    >  Si elle est activée, les options **Respecter la casse**, **Respecter les accents**, **Respecter le jeu de caractères Kana**et **Respecter la largeur** ne sont alors pas disponibles.  
  
-   **Binaire 2** permet de trier et de comparer les données Unicode en fonction des modèles binaires définis pour chaque caractère. L'ordre de tri binaire respecte la casse, c'est-à-dire que les minuscules précèdent les majuscules ; il respecte également les accents. Il s'agit de l'ordre de tri le plus rapide.  
  
-   **Respecter la casse** permet de trier et de comparer les données d’après les règles du dictionnaire de la langue ou de l’alphabet associé, et de faire la distinction entre les majuscules et les minuscules.  
  
     Si cette option n'est pas sélectionnée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu'il n'y a pas de différences entre les lettres majuscules et minuscules. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne définit pas si les lettres minuscules doivent être triées avant ou après en majuscules les lettres quand **respect de la casse** n’est pas sélectionnée.  
  
-   **Respecter les accents** permet de trier et de comparer les données d’après les règles du dictionnaire de la langue ou de l’alphabet associé, et de faire la distinction entre les lettres accentuées ou non. Par exemple, « a » n'est pas équivalent à « á ».  
  
     Si l'option n'est pas cochée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu'il n'y a pas de différences entre les lettres accentuées et non accentuées.  
  
-   **Respecter le jeu de caractères Kana** permet de trier et de comparer les données d’après les règles du dictionnaire de la langue ou de l’alphabet associé, et de faire la distinction entre les deux types de caractères japonais Kana : Hiragana et Katakana.  
  
     Si l'option n'est pas choisie, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère qu'il n'y a pas de différences entre les caractères Hiragana et Katakana.  
  
-   **Respecter la largeur** permet de trier et de comparer les données d’après les règles du dictionnaire de la langue ou de l’alphabet associé, et de faire la distinction entre un caractère sur un octet (demi-chasse) et le même caractère représenté sur deux octets (pleine chasse).  
  
     Si cette option n’est pas sélectionnée, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère que les représentations d’un même caractère sur un octet et sur deux octets sont égales.  
  
## <a name="security-properties"></a>Propriétés de sécurité  
 Cette page permet d'indiquer les comptes d'utilisateur et de groupe Windows appartenant au rôle d'administrateur du serveur pour toute instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . L'appartenance à ce rôle permet d'exécuter des tâches sur le serveur, comme créer ou traiter une base de données, modifier des propriétés du serveur, ajouter ou supprimer d'autres membres de ce rôle ou lancer une trace. Consultez [accorder des autorisations administrateur du serveur &#40;Analysis Services&#41; ](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Déterminer le mode serveur d'une instance Analysis Services](instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Configurer les propriétés du serveur dans Analysis Services](server-properties/server-properties-in-analysis-services.md)   
 [Méthodologies d'authentification prises en charge par Analysis Services](instances/authentication-methodologies-supported-by-analysis-services.md)   
 [Rôles et autorisations &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md)   
 [Langues et classements &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md)  
  
  
