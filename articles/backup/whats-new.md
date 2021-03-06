---
title: Wat is er nieuw in Azure Backup
description: Meer informatie over nieuwe functies in Azure Backup.
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: e48a7df1e42591843c30b77026a4d8656773a57d
ms.sourcegitcommit: b8eba4e733ace4eb6d33cc2c59456f550218b234
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95511507"
---
# <a name="whats-new-in-azure-backup"></a>Wat is er nieuw in Azure Backup

Azure Backup is voortdurend verbeterd en brengt nieuwe functies uit die de beveiliging van uw gegevens in azure verbeteren. Met deze nieuwe functies wordt uw gegevens bescherming uitgebreid naar nieuwe werkbelasting typen, wordt de beveiliging verbeterd en wordt de beschik baarheid van uw back-upgegevens verbeterd. Ze voegen ook nieuwe mogelijkheden voor beheer, bewaking en automatisering toe.

Meer informatie over de nieuwe releases vindt u in blad wijzers op deze pagina of door u [te abonneren op updates](https://azure.microsoft.com/updates/?query=backup).

## <a name="updates-summary"></a>Samen vatting van updates

- November 2020
  - [Incrementele back-ups voor SAP HANA data bases op virtuele Azure-machines](#incremental-backups-for-sap-hana-databases)
- September 2020
  - [Back-upcentrum](#backup-center)
  - [Back-up maken van Azure Database for PostgreSQL](#backup-azure-database-for-postgresql)
  - [Back-up en herstel van selectieve schijven](#selective-disk-backup-and-restore)
  - [Meerdere regio's herstellen voor SQL Server-en SAP HANA-data bases op virtuele machines in azure](#cross-region-restore-for-sql-server-and-sap-hana)
  - [Ondersteuning voor back-ups van Vm's met Maxi maal 32 schijven](#support-for-backup-of-vms-with-up-to-32-disks)
  - [Vereenvoudigde back-upconfiguratie-ervaring voor SQL in azure Vm's](#simpler-backup-configuration-for-sql-in-azure-vms)
  - [Back-SAP HANA in RHEL Azure Virtual Machines](#backup-sap-hana-in-rhel-azure-virtual-machines)
  - [Zone redundante opslag (ZRS) voor back-upgegevens](#zone-redundant-storage-zrs-for-backup-data)
  - [Zacht verwijderen voor SQL Server en SAP HANA workloads in azure-Vm's](#soft-delete-for-sql-server-and-sap-hana-workloads)

## <a name="incremental-backups-for-sap-hana-databases"></a>Incrementele back-ups voor SAP HANA-data bases

Azure Backup biedt nu ondersteuning voor incrementele back-ups voor SAP HANA-data bases die worden gehost op virtuele machines van Azure. Hierdoor kunt u sneller en rendabelere back-ups van uw SAP HANA gegevens maken.

Zie voor meer informatie [diverse opties die beschikbaar zijn tijdens het maken van een back-upbeleid](sap-hana-faq-backup-azure-vm.md#policy) en [het maken van een back-upbeleid voor SAP Hana data bases](tutorial-backup-sap-hana-db.md#creating-a-backup-policy).

## <a name="backup-center"></a>Back-upcentrum

Azure Backup heeft een nieuwe systeem eigen beheer mogelijkheid voor het beheren van uw volledige back-ups vanuit een centrale console. Back-upcentrum biedt u de mogelijkheid om gegevens beveiliging op schaal te bewaken, bedienen, beheren en optimaliseren op een uniforme manier die overeenkomt met de systeem eigen beheer ervaringen van Azure.

Met backup Center krijgt u een geaggregeerde weer gave van uw inventaris in abonnementen, locaties, resource groepen, kluizen en zelfs tenants met behulp van Azure Lighthouse. Het Back-upcentrum is ook een onderhouds centrum waarmee u uw back-upgerelateerde activiteiten kunt activeren, zoals het configureren van back-ups, herstel, het maken van beleids regels of kluizen, op één plek. Daarnaast kunt u met een naadloze integratie met Azure Policy uw omgeving beheren en de naleving van een back-upperspectief bijhouden. In de ingebouwde Azure-beleids regels die specifiek zijn voor Azure Backup, kunt u ook back-ups op schaal configureren.

Zie [overzicht van Back-upcentrum](backup-center-overview.md)voor meer informatie.

## <a name="backup-azure-database-for-postgresql"></a>Back-up maken van Azure Database for PostgreSQL

Azure Backup-en Azure Data Base-Services hebben samen een bedrijfs klasse-back-upoplossing voor Azure PostgreSQL (nu beschikbaar als preview-versie). U kunt nu voldoen aan de vereisten voor gegevens beveiliging en naleving met een back-upbeleid dat door de klant wordt beheerd, waarmee back-ups tot wel tien jaar kunnen worden bewaard. Hiermee hebt u gedetailleerde controle over het beheer van de back-up-en herstel bewerkingen op het afzonderlijke database niveau. Op dezelfde manier kunt u met gemak herstellen over PostgreSQL-versies of naar Blob Storage.

Zie [Azure database for PostgreSQL backup](backup-azure-database-postgresql.md)voor meer informatie.

## <a name="selective-disk-backup-and-restore"></a>Back-up en herstel van selectieve schijven

Azure Backup biedt ondersteuning voor het maken van een back-up van alle schijven (besturings systeem en gegevens) in een virtuele machine met behulp van de back-upoplossing voor VM'S. Nu kunt u, met behulp van de functies voor het maken en herstellen van selectieve schijven, een back-up maken van een subset van de gegevens schijven in een VM. Dit biedt een efficiënte en rendabele oplossing voor uw back-up-en herstel behoeften. Elk herstel punt bevat alleen de schijven die zijn opgenomen in de back-upbewerking.

Zie [selectief schijf back-ups maken en herstellen voor Azure virtual machines](selective-disk-backup-restore.md)voor meer informatie.

## <a name="cross-region-restore-for-sql-server-and-sap-hana"></a>Meerdere regio's herstellen voor SQL Server en SAP HANA

Met de introductie van meerdere regio's herstellen kunt u nu herstel bewerkingen in een secundaire regio initiëren om problemen met de uitval tijd in een primaire regio voor uw omgeving te verhelpen. Dit maakt de secundaire regio volledig beheerd. Azure Backup maakt gebruik van de back-upgegevens die worden gerepliceerd naar de secundaire regio voor dergelijke herstel bewerkingen.

Naast ondersteuning voor het herstel van meerdere regio's voor virtuele Azure-machines is de functie uitgebreid voor het herstellen van SQL-en SAP HANA data bases in azure virtual machines.

Zie voor meer informatie [meerdere regio's herstellen voor SQL-data bases](restore-sql-database-azure-vm.md#cross-region-restore) en het [herstellen van meerdere regio's voor SAP Hana-data bases](sap-hana-db-restore.md#cross-region-restore).

## <a name="support-for-backup-of-vms-with-up-to-32-disks"></a>Ondersteuning voor back-ups van Vm's met Maxi maal 32 schijven

Tot nu toe heeft Azure Backup 16 beheerde schijven per VM ondersteund. Azure Backup ondersteunt nu back-ups van Maxi maal 32 Managed disks per VM.

Zie de [ondersteunings matrix voor VM-opslag](backup-support-matrix-iaas.md#vm-storage-support)voor meer informatie.

## <a name="simpler-backup-configuration-for-sql-in-azure-vms"></a>Eenvoudigere back-upconfiguratie voor SQL in azure-Vm's

Het configureren van back-ups voor uw SQL Server in azure-Vm's is nu nog eenvoudiger dankzij de configuratie van inline-back-ups die is geïntegreerd in het deel venster VM van de Azure Portal. In slechts een paar stappen kunt u back-up van uw SQL Server inschakelen om alle bestaande data bases te beveiligen, evenals de bestanden die in de toekomst worden toegevoegd.

Zie [een back-up maken van een SQL Server in het deel venster VM](backup-sql-server-vm-from-vm-pane.md)voor meer informatie.

## <a name="backup-sap-hana-in-rhel-azure-virtual-machines"></a>Back-SAP HANA in RHEL Azure virtual machines

Azure Backup is de systeem eigen back-upoplossing voor Azure en is BackInt gecertificeerd door SAP. Azure Backup hebt nu ondersteuning toegevoegd voor Red Hat Enterprise Linux (RHEL), een van de meest gebruikte Linux-besturings systemen met SAP HANA.

Zie de [ondersteunings matrix voor SAP Hana database back-upscenario](sap-hana-backup-support-matrix.md#scenario-support)voor meer informatie.

## <a name="zone-redundant-storage-zrs-for-backup-data"></a>Zone redundante opslag (ZRS) voor back-upgegevens

Azure Storage biedt een uitstekende verhouding tussen hoge prestaties, hoge Beschik baarheid en hoge gegevens tolerantie met de verschillende opties voor redundantie. Met Azure Backup kunt u deze voor delen ook uitbreiden naar back-upgegevens, met opties voor het opslaan van uw back-ups in lokaal redundante opslag (LRS) en geografisch redundante opslag (GRS). Nu zijn er extra duurzaamheids opties met de toegevoegde ondersteuning voor zone redundant Storage (ZRS).

Zie [opslag redundantie instellen voor de Recovery Services kluis](backup-create-rs-vault.md#set-storage-redundancy)voor meer informatie.

## <a name="soft-delete-for-sql-server-and-sap-hana-workloads"></a>Zacht verwijderen voor SQL Server en SAP HANA werk belastingen

Problemen met betrekking tot beveiligings problemen, zoals malware, Ransomware en indringing, worden verhoogd. Deze beveiligings problemen kunnen kostbaar zijn, zowel voor geld als voor gegevens. Azure Backup biedt beveiligings functies die u helpen bij het beveiligen van back-upgegevens, zelfs na verwijdering.

Een dergelijke functie is zacht verwijderen. Met zacht verwijderen, zelfs als een schadelijke actor een back-up verwijdert (of als er per ongeluk back-upgegevens worden verwijderd), worden de back-upgegevens 14 extra dagen bewaard, zodat het back-upitem zonder gegevens verlies kan worden hersteld. De extra 14 dagen voor het bewaren van back-upgegevens in de status ' voorlopig verwijderen ' maken geen kosten voor u.

Nu wordt de ondersteuning voor het uitvoeren van tijdelijke verwijderingen voor Azure-Vm's, SQL Server en SAP HANA werk belastingen in azure Vm's ook beveiligd met een tijdelijke verwijdering.

Zie [voorlopig verwijderen voor SQL Server in azure VM en SAP Hana in azure VM-workloads](soft-delete-sql-saphana-in-azure-vm.md)voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

- [Azure Backup richtlijnen en best practices](guidance-best-practices.md)
