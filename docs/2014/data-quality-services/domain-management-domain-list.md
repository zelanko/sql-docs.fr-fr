---
title: 'Gestion de l’arborescence du domaine : Liste des domaines | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.domainlist.f1
ms.assetid: 8df305f0-97ea-4226-811b-979ed862e1f0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c0dfc543659bdb8476d880bbe6021d0f3fd27bfd
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032486"
---
# <a name="domain-management-domain-list"></a>Gestion de l'arborescence du domaine : Liste des domaines
  Cette rubrique décrit les contrôles dans la liste des domaines de la page **Gestion de l'arborescence du domaine** dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Utilisez ce volet pour sélectionner un domaine sur lequel effectuer des opérations de gestion. Le même volet est utilisé pour toutes les pages à onglets dans la page **Gestion de l'arborescence du domaine** .  
  
## <a name="options"></a>Options  
  
### <a name="domains-list"></a>Liste des domaines  
 **Domaine**  
 Cette liste affiche tous les domaines dans la base de connaissances. Les opérations que vous effectuez dans les pages à onglets dans le volet droit sont exécutées sur le domaine sélectionné dans la liste. Pour plus d'informations, consultez  
  
 **Créer un domaine composite**  
 Créez un nouveau domaine composite dans la base de connaissances. Cette commande affiche la boîte de dialogue **Créer un domaine composite** . Cette commande est disponible en cliquant avec le bouton droit sur un domaine ou en cliquant sur l'icône au-dessus de la liste des domaines. Pour plus d’informations, consultez [Créer un domaine composite](../../2014/data-quality-services/create-a-composite-domain.md).  
  
 **Créer un domaine**  
 Créez un nouveau domaine dans la base de connaissances. Cette commande affiche la boîte de dialogue **Créer un domaine** . Cette commande est disponible en cliquant avec le bouton droit sur un domaine ou en cliquant sur l'icône au-dessus de la liste des domaines. Pour plus d’informations, consultez [Créer un domaine](../../2014/data-quality-services/create-a-domain.md).  
  
 **Créer une copie du domaine sélectionné**  
 Créez une copie exacte du domaine sélectionné, puis ajoutez-la à la base de connaissances. Son nom est le nom du domaine à partir duquel elle a été créée, avec « – Copie » ajouté à la fin du nom. Cette commande est disponible en cliquant avec le bouton droit sur un domaine, puis en cliquant sur **Créer une copie**, ou en cliquant sur l'icône au-dessus de la liste des domaines. Elle n'est pas disponible pour un domaine composite.  
  
 **Importer un domaine à partir d'un fichier de données**  
 Importez un domaine à partir d'un fichier .dqs. Cette commande affiche la boîte de dialogue **Importer à partir d'un fichier de données** qui vous permet de parcourir le système de fichiers et de sélectionner un fichier .dqs pour un seul domaine ou un domaine composite. Cette commande est disponible en cliquant sur l'icône au-dessus de la liste des domaines. Pour plus d’informations, consultez [Importez un domaine à partir d'un fichier .dqs](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md).  
  
 **Supprimer le domaine**  
 Supprimez le domaine sélectionné de la base de connaissances. Cette commande affiche la boîte de dialogue **SQL Server Data Quality Services** . Si vous cliquez sur **Oui**, le domaine et toutes ses données seront supprimés définitivement. Cette commande est disponible en cliquant avec le bouton droit sur un domaine ou en cliquant sur l'icône au-dessus de la liste des domaines.  
  
 **Créer un domaine lié**  
 Créez un domaine lié au domaine sélectionné. Cette commande affiche la boîte de dialogue **Créer un domaine** . Cette commande est disponible en cliquant avec le bouton droit sur un domaine, puis en cliquant sur **Créer un domaine lié** . Le domaine avec lequel vous établissez la liaison s'affiche dans la boîte de dialogue Créer un domaine. La commande n'est pas disponible pour un domaine composite. Il n'existe aucune commande disponible pour dissocier deux domaines ; pour cela, supprimez le domaine lié. Un domaine lié ne peut pas être lié à un domaine lié. Pour plus d’informations, consultez [Créer un domaine lié](../../2014/data-quality-services/create-a-linked-domain.md).  
  
 Un domaine lié a les mêmes valeurs que le domaine auquel il est lié. Seul le nom et les propriétés du domaine sont différents. Si vous modifiez une règle de domaine, une valeur de domaine, une liaison de données de référence ou une relation à base de termes dans le domaine auquel il est lié, la règle de domaine, la valeur de domaine, la liaison de données de référence ou la relation à base de termes dans le domaine lié changent également. De plus, si vous modifiez une valeur du domaine lié, la modification est également apportée au domaine auquel il est lié.  
  
 **Exporter la base de connaissances**  
 Exportez la base de connaissances entière vers un fichier .dqs. Cette commande affiche la boîte de dialogue **Exporter vers un fichier de données** . Cette commande est disponible en cliquant sur l'icône **Exporter des données de Base de connaissances** en haut de la page, ou sous **Exporter** dans le menu contextuel des domaines dans le volet de la liste des domaines. Pour plus d’informations, consultez [Exporter une base de connaissances dans un fichier .dqs](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md).  
  
 **Exporter le domaine**  
 Exportez le domaine vers un fichier .dqs. Cette commande affiche la boîte de dialogue **Exporter vers un fichier de données** . Cette commande est disponible dans le menu **Exporter** dans la barre de menus en haut de la page, ou en cliquant avec le bouton droit dans le volet de la liste des domaines. Pour plus d’informations, consultez [Exporter un domaine vers un fichier .dqs](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
  
