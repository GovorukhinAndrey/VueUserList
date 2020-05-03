<template>
  <div>
    <div v-if="!list.length" class="alert alert-warning">
      Нет пользователей
    </div>
    <user-list v-else :list="list" @click="removeFromList"></user-list>

    <button type="button" @click="loadData">
      Загрузить данные
    </button>
  </div>
</template>

<script>
import UserList from '@/components/UserList.vue';

export default {
  name: 'UserListPage',
  components: {
    UserList,
  },
  data: () => ({
    list: [],
  }),
  methods: {
    loadData() {
      this.list = [
        {
          id: 0,
          isActive: false,
          balance: '$3,699.59',
          picture: 'http://placehold.it/128x128',
          age: 25,
          accessLevel: 'user',
          firstName: 'Cervantes',
          lastName: 'Farley',
          company: 'ISOLOGIA',
          email: 'cervantes.farley@isologia.co.uk',
          phone: '+7 (856) 498-2247',
          address: '452 Milford Street, Guthrie, New Jersey, 1360',
          about:
            'Nostrud duis dolor cupidatat ad reprehenderit est culpa labore ipsum eu cupidatat ea dolore culpa. In elit est id tempor enim elit culpa consequat exercitation sit mollit esse eiusmod nisi. Labore adipisicing cupidatat occaecat est adipisicing occaecat amet occaecat non anim. Tempor cillum voluptate ut mollit aute cupidatat adipisicing et aliquip esse ullamco laboris.',
          registered: '30.12.2019',
        },
        {
          id: 1,
          isActive: true,
          balance: '$2,994.22',
          picture: 'http://placehold.it/128x128',
          age: 31,
          accessLevel: 'user',
          firstName: 'Massey',
          lastName: 'Waller',
          company: 'CUBIX',
          email: 'massey.waller@cubix.biz',
          phone: '+7 (880) 405-2841',
          address: '700 Gerry Street, Vaughn, South Carolina, 9397',
          about:
            'In nisi incididunt dolore eiusmod. Cupidatat nisi qui ea eu sit in Lorem nulla sunt enim laborum laboris commodo dolore. Ea dolor aliquip laborum veniam et enim. Dolore fugiat est consequat pariatur et anim consectetur aliquip Lorem ullamco ullamco anim. Id eiusmod tempor tempor sunt labore nisi ea ullamco mollit excepteur amet. Ea non do qui irure voluptate tempor ex sit est exercitation veniam. Minim et commodo do veniam magna ullamco tempor laboris est nulla.',
          registered: '25.03.2018',
        },
        {
          id: 2,
          isActive: false,
          balance: '$3,043.20',
          picture: 'http://placehold.it/128x128',
          age: 40,
          accessLevel: 'guest',
          firstName: 'Kelly',
          lastName: 'Osborne',
          company: 'ZILCH',
          email: 'kelly.osborne@zilch.com',
          phone: '+7 (907) 559-3131',
          address: '251 Louisa Street, Comptche, Hawaii, 7208',
          about:
            'Excepteur id quis laborum dolor est do deserunt duis dolor nostrud voluptate. Aliquip ipsum quis elit sint quis eiusmod. Ex commodo laboris elit anim veniam est laboris commodo laboris irure incididunt. Officia occaecat proident sit fugiat commodo labore dolore eiusmod. Duis ullamco occaecat laborum ea consequat magna incididunt minim anim est officia proident do. Commodo voluptate esse qui veniam dolor ex. Non ex irure commodo deserunt aliquip mollit esse labore eiusmod aliqua esse consectetur enim esse.',
          registered: '17.12.2019',
        },
        {
          id: 3,
          isActive: false,
          balance: '$1,687.42',
          picture: 'http://placehold.it/128x128',
          age: 40,
          accessLevel: 'guest',
          firstName: 'Leach',
          lastName: 'Gonzalez',
          company: 'ZINCA',
          email: 'leach.gonzalez@zinca.me',
          phone: '+7 (915) 413-3775',
          address: '151 Senator Street, Baker, Minnesota, 5684',
          about:
            'Pariatur sint dolore officia laborum. Ad cillum minim esse ad laboris consequat commodo velit labore. Voluptate nulla laboris anim commodo laboris deserunt mollit ipsum consequat voluptate. Incididunt voluptate anim mollit dolore. Adipisicing ullamco sit mollit quis pariatur sint magna irure.',
          registered: '25.06.2016',
        },
        {
          id: 4,
          isActive: true,
          balance: '$2,917.13',
          picture: 'http://placehold.it/128x128',
          age: 24,
          accessLevel: 'user',
          firstName: 'Valenzuela',
          lastName: 'Monroe',
          company: 'ORBALIX',
          email: 'valenzuela.monroe@orbalix.tv',
          phone: '+7 (814) 438-2938',
          address: '263 Schenck Avenue, Edgewater, Mississippi, 9327',
          about:
            'Et et occaecat aute aliquip enim exercitation dolor irure reprehenderit magna ut in excepteur irure. Duis proident nostrud dolore culpa nulla nostrud aliqua officia sit commodo laboris consequat. Consequat esse pariatur mollit enim enim consectetur voluptate et nulla adipisicing aute ex sunt ut. Cupidatat duis eiusmod id culpa ad anim sunt esse adipisicing occaecat esse do. In duis adipisicing dolor pariatur et aliqua exercitation Lorem cillum.',
          registered: '23.07.2017',
        },
        {
          id: 5,
          isActive: false,
          balance: '$2,633.48',
          picture: 'http://placehold.it/128x128',
          age: 34,
          accessLevel: 'user',
          firstName: 'Larsen',
          lastName: 'Dorsey',
          company: 'TERRAGO',
          email: 'larsen.dorsey@terrago.ca',
          phone: '+7 (868) 560-2394',
          address: '572 Cranberry Street, Hebron, Indiana, 2013',
          about:
            'Commodo cillum aute irure aliqua veniam eu commodo deserunt tempor duis laboris culpa officia. Nulla sint dolore pariatur veniam consectetur non eu aliqua est eiusmod exercitation voluptate. Cupidatat excepteur mollit irure do consequat laboris qui culpa. Do reprehenderit pariatur eu fugiat occaecat mollit enim eu ullamco consectetur.',
          registered: '22.02.2019',
        },
        {
          id: 6,
          isActive: true,
          balance: '$1,402.96',
          picture: 'http://placehold.it/128x128',
          age: 39,
          accessLevel: 'user',
          firstName: 'Mara',
          lastName: 'Estes',
          company: 'TUBALUM',
          email: 'mara.estes@tubalum.org',
          phone: '+7 (916) 500-2156',
          address: '742 Clifton Place, Tryon, Virgin Islands, 9956',
          about:
            'Non velit minim ut pariatur velit sint reprehenderit ad ea ut aliquip minim sunt. Tempor anim ut consectetur aliqua do. Ea ut ipsum laboris esse est deserunt commodo non consequat. Adipisicing deserunt nostrud in elit sunt cillum eiusmod est adipisicing deserunt elit amet commodo.',
          registered: '24.07.2015',
        },
        {
          id: 7,
          isActive: true,
          balance: '$2,756.25',
          picture: 'http://placehold.it/128x128',
          age: 27,
          accessLevel: 'guest',
          firstName: 'Dodson',
          lastName: 'Henson',
          company: 'UPDAT',
          email: 'dodson.henson@updat.net',
          phone: '+7 (845) 539-2455',
          address: '588 Henry Street, Thornport, Rhode Island, 4135',
          about:
            'Veniam culpa adipisicing velit veniam esse. Proident culpa elit incididunt dolore tempor ea commodo non eiusmod Lorem. Minim non elit nisi consectetur consectetur laboris sit in adipisicing nostrud voluptate. Et laborum ipsum enim proident consectetur consectetur labore enim nulla minim dolor.',
          registered: '22.07.2019',
        },
        {
          id: 8,
          isActive: false,
          balance: '$3,689.59',
          picture: 'http://placehold.it/128x128',
          age: 33,
          accessLevel: 'guest',
          firstName: 'Monroe',
          lastName: 'Burt',
          company: 'ENERSAVE',
          email: 'monroe.burt@enersave.info',
          phone: '+7 (836) 463-3564',
          address: '736 Stockton Street, Crumpler, Michigan, 4161',
          about:
            'Qui aliquip laboris aute ipsum nulla voluptate aliqua dolore ad reprehenderit aute qui. Ipsum duis dolor ea excepteur sint consequat anim ea culpa sunt proident. Reprehenderit duis in laborum sint ipsum sint deserunt anim. Deserunt consequat nostrud id Lorem nostrud laborum voluptate cillum ad. Id nisi nulla cillum eiusmod incididunt consequat pariatur in non adipisicing. Cillum Lorem non irure nulla mollit aliquip duis sint. Do labore ea non Lorem qui consequat consectetur ea irure culpa.',
          registered: '03.02.2015',
        },
        {
          id: 9,
          isActive: false,
          balance: '$2,498.17',
          picture: 'http://placehold.it/128x128',
          age: 28,
          accessLevel: 'user',
          firstName: 'Garrison',
          lastName: 'Mccarthy',
          company: 'SNIPS',
          email: 'garrison.mccarthy@snips.name',
          phone: '+7 (987) 593-3223',
          address: '587 Degraw Street, Bellfountain, Idaho, 3612',
          about:
            'Ad tempor enim ipsum exercitation enim amet laborum. Qui sit anim ex mollit laborum dolor non incididunt ex dolore nulla voluptate velit. Sunt consequat Lorem velit excepteur incididunt mollit aute adipisicing aliqua ipsum nulla do eu. Qui et proident sit reprehenderit adipisicing aliquip officia nisi magna non.',
          registered: '28.04.2015',
        },
        {
          id: 10,
          isActive: true,
          balance: '$3,794.40',
          picture: 'http://placehold.it/128x128',
          age: 25,
          accessLevel: 'guest',
          firstName: 'Amelia',
          lastName: 'Cooley',
          company: 'DIGIRANG',
          email: 'amelia.cooley@digirang.io',
          phone: '+7 (820) 588-2574',
          address: '229 Landis Court, Wauhillau, New Mexico, 5393',
          about:
            'Pariatur ea dolor pariatur dolore exercitation excepteur. Tempor veniam exercitation non adipisicing. Officia ut ullamco non laboris labore veniam magna in incididunt irure.',
          registered: '30.03.2015',
        },
      ];
    },
    removeFromList(id) {
      this.list = this.list.filter(item => item.id !== id);
    },
  },
};
</script>

<style></style>
