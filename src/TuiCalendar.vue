<script>
import TuiCalendar from 'tui-calendar'

const kebabCase = string =>
  string
    .replace(/([a-z])([A-Z])/g, '$1-$2')
    .replace(/\s+/g, '-')
    .toLowerCase()

const events = [
  'beforeCreateSchedule',
  'afterRenderSchedule',
  'beforeUpdateSchedule',
  'beforeDeleteSchedule',
  'clickSchedule',
  'clickDayname'
]

export default {
  props: {
    tag: {
      type: String,
      default: 'div'
    },

    schedules: {
      type: Array,
      required: true
    },

    options: {
      type: Object,
      default: () => ({})
    }
  },

  watch: {
    schedules: {
      handler: 'render',
      deep: true
    },
    options: {
      handler: 'render',
      deep: true
    }
  },

  methods: {
    render () {
      this.calendar.clear()
      this.calendar.createSchedules(this.schedules)
      this.calendar.render()
    },

    registerEvents () {
      events.forEach(event => {
        this.registerEvent(event, (...args) => {
          this.$emit(kebabCase(event), ...args)
        })
      })
    },

    registerEvent (event, callback) {
      this.calendar.on(event, callback)
    },

    fireMethod (method, ...args) {
      return this.calendar[method](...args)
    }
  },

  mounted () {
    this.calendar = new TuiCalendar(this.$el, this.options)

    this.registerEvents()
    this.render()
  },

  render (h) {
    return h(this.tag)
  },

  beforeDestroy () {
    this.calendar.destroy()
  }
}
</script>
