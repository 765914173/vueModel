<<template>
    <div>
        Welcome to manage system
        <footer-nav v-bind:class="{'isIndex':isNowPage}"></footer-nav>
    </div>
</template>

<script>
import FooterNav from '../../components/footer'
export default {
  components: {
      FooterNav
  },
  data(){
      return{
          isNowPage:true,
          peoples:[{'name':'Jack'},{'name':'Sam'}]
      }
  }
}
</script>

