<template>
  <div>
    <div class="class">
      <el-row :gutter="20">
        <el-col
          :xs="12"
          :sm="6">
          <div
            class="class__card"
            @click="show('6')">
            <span class="class__card__name text-neon-green">6</span>
          </div>
        </el-col>
        <el-col
          :xs="12"
          :sm="6">
          <div
            class="class__card"
            @click="show('7')">
            <span class="class__card__name text-neon-yellow">7</span>
          </div>
        </el-col>
        <el-col
          :xs="12"
          :sm="6">
          <div
            class="class__card"
            @click="show('8')">
            <span class="class__card__name text-neon-pink">8</span>
          </div>
        </el-col>
        <el-col
          :xs="12"
          :sm="6">
          <div
            class="class__card"
            @click="show('9')">
            <span class="class__card__name text-neon-purple">9</span>
          </div>
        </el-col>
      </el-row>
    </div>
    <div class="syllabus">
      <modal
        v-for="(item, index) in syllabus"
        :key="index"
        :name="item.grade"
        :adaptive="true"
        :scrollable="true"
        :resizable="true"
        width="80%"
        height="auto">
        <div
          v-for="(book, index) in item.books"
          :key="index"
          class="syllabus__card">
          <div class="syllabus__copy">
            <h2
              :class="['text-' + book.theme]"
              class="syllabus__name">{{ book.title }}</h2>
            <p class="syllabus__description">{{ book.description }}</p>
            <button
              v-for="(url, index) in book.urls"
              :key="index"
              :data-url="url.link"
              :data-modal="item.grade"
              :class="['btn--' + book.theme]"
              class="btn btn--round"
              @click="goTo($event)">{{ url.name }}</button>
          </div>
          <img
            :src="require(`~/assets/images/intro/${book.img}`)"
            :alt="book.title"
            class="syllabus__img">
        </div>
      </modal>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      syllabus: [{
        grade: '6',
        books: [{
          id: '5b15e581e8db3027119530bc',
          title: 'Lịch sử',
          description: 'Chương trình lịch sử lớp 6 gồm 3 phần. Phần mở đầu giới thiệu các bài học chung sơ lược về lịch sử. Phần I giới thiệu lịch sử thế giới từ khi loài người xuất hiện đến cuối thời cổ đại. Phần II nói về lịch sử Việt Nam giới thiệu lịch sử dân tộc từ thời nguyên thuỷ đến thế kỷ X.',
          urls: [{
            name: 'Học ngay',
            link: 'course/history-6'
          }, {
            name: 'Dòng sự kiện lịch sử',
            link: '/timeline'
          }],
          img: 'history-1.jpg',
          theme: 'brown'
        }, {
          id: '5b2dbbc07a45863cf280ef50',
          title: 'Địa lí',
          description: 'Chương trình địa lý lớp 6 gồm 2 chương lớn là Trái Đất và các thành phần tự nhiên của Trái Đất. Trong đó, chương Trái đất sẽ học về vị trí, hình dạng, kích thước, các hiện tượng của trái đất,….chương các thành phần tự nhiên của Trái đất sẽ cung cấp những kiến thức về tác động của nội lực, ngoại lực, khí hậu trên trái đất,…',
          urls: [{
            name: 'Học ngay',
            link: 'course/geography-6'
          }, {
            name: 'Bản đồ địa lí tương tác',
            link: '/geomap'
          }],
          img: 'geography-1.jpg',
          theme: 'green'
        }]
      }, {
        grade: '7',
        books: [{
          id: '5b15e588e8db3027119530bd',
          title: 'Lịch sử',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam bibendum justo ut nibh interdum, sit amet molestie ex lacinia. Suspendisse sagittis nunc quis lorem ornare, et varius purus vulputate. Aenean vitae tempus tellus. Nam et mattis quam, vitae molestie mi. Proin ac orci orci.',
          urls: [{
            name: 'Phần 1',
            link: 'course/history-7-p1'
          }, {
            name: 'Phần 2',
            link: 'course/history-7-p2'
          }, {
            name: 'Dòng sự kiện lịch sử',
            link: '/timeline'
          }],
          img: 'history-1.jpg',
          theme: 'brown'
        }, {
          id: '5b2dbc027a45863cf280ef51',
          title: 'Địa lí',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam bibendum justo ut nibh interdum, sit amet molestie ex lacinia. Suspendisse sagittis nunc quis lorem ornare, et varius purus vulputate. Aenean vitae tempus tellus. Nam et mattis quam, vitae molestie mi. Proin ac orci orci.',
          urls: [{
            name: 'Phần 1',
            link: 'course/geography-7-p1'
          }, {
            name: 'Phần 2',
            link: 'course/geography-7-p2'
          }, {
            name: 'Bản đồ địa lí tương tác',
            link: '/geomap'
          }],
          img: 'geography-1.jpg',
          theme: 'green'
        }]
      }, {
        grade: '8',
        books: [{
          id: '5b15e58ee8db3027119530be',
          title: 'Lịch sử',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam bibendum justo ut nibh interdum, sit amet molestie ex lacinia. Suspendisse sagittis nunc quis lorem ornare, et varius purus vulputate. Aenean vitae tempus tellus. Nam et mattis quam, vitae molestie mi. Proin ac orci orci.',
          urls: [{
            name: 'Phần 1',
            link: 'course/history-8-p1'
          }, {
            name: 'Phần 2',
            link: 'course/history-8-p2'
          }, {
            name: 'Dòng sự kiện lịch sử',
            link: '/timeline'
          }],
          img: 'history-1.jpg',
          theme: 'brown'
        }, {
          id: '5b2dbc157a45863cf280ef52',
          title: 'Địa lí',
          description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam bibendum justo ut nibh interdum, sit amet molestie ex lacinia. Suspendisse sagittis nunc quis lorem ornare, et varius purus vulputate. Aenean vitae tempus tellus. Nam et mattis quam, vitae molestie mi. Proin ac orci orci.',
          urls: [{
            name: 'Phần 1',
            link: 'course/geography-8-p1'
          }, {
            name: 'Phần 2',
            link: 'course/geography-8-p2'
          }, {
            name: 'Bản đồ địa lí tương tác',
            link: '/geomap'
          }],
          img: 'geography-1.jpg',
          theme: 'green'
        }]
      }]
    }
  },
  methods: {
    show (modal) {
      this.$modal.show(modal)
    },
    goTo (event) {
      this.$modal.hide(event.target.dataset.modal)
      this.$router.push({ path: event.target.dataset.url })
    }
  }
}
</script>

<style lang="scss">
.class {
  margin-bottom: rem(20);

  &__card {
    @include flex-center;

    background-color: $color-white;
    border-radius: 8px;
    box-shadow: $box-shadow-heavy;
    cursor: pointer;
    height: 200px;
    margin-bottom: rem(20);
    // opacity: 0.8;

    &:hover {
      box-shadow: $box-shadow-normal;
      // opacity: 1;
    }

    &__name {
      font-size: rem(100);
      font-weight: $font-weight-bold;
    }
  }
}

.syllabus {
  &__badge {
    color: $color-white;
    font-weight: $font-weight-normal;
    line-height: rem(30);
    padding-right: rem(12);
    position: absolute;
    top: rem(12);
    left: 0;
    text-indent: rem(25);

    &::after {
      content: "";
      border-width: 1.75rem 1rem 0 0;
      border-style: solid;
      position: absolute;
      top: 0;
      right: -1rem;
      transform: rotate(1turn);
      width: 0;
      height: 0;
    }

    &--brown {
      background-image: linear-gradient(to right, #605c3c, #a9761b);

      &::after {
        border-color: #a9761b transparent transparent transparent;
      }
    }

    &--green {
      background-image: linear-gradient(90deg, #02b3e4 0, #02ccba);

      &::after {
        border-color: #02ccba transparent transparent transparent;
      }
    }
  }

  &__card {
    padding: 0 rem(30);
    position: relative;

    @include media(">=sm") {
      display: flex;
      align-items: flex-start;
      height: 300px;
    }

    & + & {
      margin-top: rem(20);
    }
  }

  &__copy {
    padding: rem(40) rem(15);
    position: relative;

    @include media(">=sm") {
      flex-grow: 9999;
      width: 50%;
    }
  }

  &__cta {
    font-size: $font-size-6;
    font-weight: $font-weight-semi;
    text-transform: uppercase;
  }

  &__description {
    color: rgba($color: $color-text, $alpha: 0.8);
    margin-bottom: rem(20);
  }

  &__img {
    display: none;

    @include media(">=sm") {
      border-radius: 8px;
      box-shadow: $box-shadow-heavy;
      display: block;
      flex-grow: 1;
      max-width: 50%;
      height: 100%;
    }
  }

  &__name {
    font-size: $font-size-3;
    font-weight: $font-weight-bold;
    letter-spacing: 2px;
    margin-top: rem(20);
    margin-bottom: rem(10);
    text-transform: uppercase;
  }
}
</style>
