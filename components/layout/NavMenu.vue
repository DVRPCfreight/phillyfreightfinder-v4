<script>
/**
 * Component developed from https://github.com/RGRU/vue-simple-menu
 */
import NavMenuItem from './NavMenuItem.vue'

export default {
  name: 'NavMenu',
  components: {
    'nav-menu-item': NavMenuItem
  },
  props: {
    sourceMenuData: {
      type: Object,
      required: true
    },
    defaultName: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      list: []
    }
  },
  mounted () {
    if (this.sourceMenuData) {
      this.list = this.generateBranch(this.sourceMenuData)
    }
  },
  watch: {
    sourceMenuData () {
      this.list = this.generateBranch(this.sourceMenuData)
    }
  },
  methods: {
    /**
     * generateBranch - recursive function for generate menu branch
     *
     * @param  {object} menuBranch branc menu for precessing
     * @return {array} complete menu data
     */
    generateBranch (menuBranch) {
      return Object.keys(menuBranch).reduce((acc, item) => {
        let menuItem = {...menuBranch[item]}
        // If have child list items,
        // generate child branch
        if (menuItem.list) menuItem.list = this.generateBranch(menuItem.list)
        // If item need expand behavoir
        // add property
        if (menuItem.list && !menuItem.uri) {
          menuItem.expand = true
          menuItem.expanded = typeof menuItem.expanded === 'boolean' ? menuItem.expanded : true
        }
        return acc.concat(menuItem)
      }, [])
    }
  },
  template: '<nav-menu-item :menu="list" />'
}
</script>